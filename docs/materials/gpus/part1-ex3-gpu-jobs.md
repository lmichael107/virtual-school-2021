---
status: testing
---

GPU Exercise 1.3: Running a GPU job
===================================

To ensure that our job runs on a resource with an available GPU, all we need to
do is update two lines in the submit file. First, set `request_gpus = 1`. This tells
HTCondor that a GPU is needed to run this job. Second, we need to specify a GPU
enabled container image. This can be done by adding 
`+SingularityImage = "/cvmfs/singularity.opensciencegrid.org/opensciencegrid/tensorflow-gpu:2.3"`
to the submit file. Note that in the previous section, the container image specified was not
GPU enabled. The updated submit file with the changes mentioned above is named `gpu-job.submit`
and contains the following contents:

    universe = vanilla

    # Job requirements - ensure we are running on a Singularity enabled
    # node and have enough resources to execute our code
    # Tensorflow also requires AVX instruction set and a newer host kernel
    Requirements = HAS_SINGULARITY == True && HAS_AVX2 == True && OSG_HOST_KERNEL_VERSION >= 31000
    request_cpus = 1
    request_gpus = 1
    request_memory = 1 GB
    request_disk = 1 GB

    # Container image to run the job in
    +SingularityImage = "/cvmfs/singularity.opensciencegrid.org/opensciencegrid/tensorflow-gpu:2.3"

    # Executable is the program your job will run It's often useful
    # to create a shell script to "wrap" your actual work.
    Executable = job-wrapper.sh
    Arguments =

    # Inputs/outputs - in this case we just need our python code.
    # If you leave out transfer_output_files, all generated files comes back
    transfer_input_files = test.py
    #transfer_output_files =

    # Error and output are the error and output channels from your job
    # that HTCondor returns from the remote host.
    Error = $(Cluster).$(Process).error
    Output = $(Cluster).$(Process).output

    # The LOG file is where HTCondor places information about your
    # job's status, success, and resource consumption.
    Log = $(Cluster).log

    # Send the job to Held state on failure.
    #on_exit_hold = (ExitBySignal == True) || (ExitCode != 0)

    # Periodically retry the jobs every 1 hour, up to a maximum of 5 retries.
    #periodic_release =  (NumJobStarts < 5) && ((CurrentTime - EnteredCurrentStatus) > 60*60)

    # queue is the "start button" - it launches any jobs that have been
    # specified thus far.
    queue 1


Submit this job with the command `condor_submit gpu-job.submit`. Once the job is complete, check
the `.out` file for a line stating that the code was run with GPU. You should see something similar
to:


    2021-02-02 23:25:19.022467: I tensorflow/core/common_runtime/eager/execute.cc:611] Executing op MatMul in device /job:localhost/replica:0/task:0/device:GPU:0


The `GPU:0` part of the log statement above shows that a GPU was found and used for the computation.

GPUs on the Open Science Pool
-----------------------------

Curious about what GPUs make up the Open Science Pool? 
Run `condor_status -const 'gpus >= 1' -af CUDADeviceName | sort | uniq -c` to find out. 
Which GPU models are most common? 

