---
status: testing
---

GPU Exercise 1.2: Running a CPU job
===================================

If Tensorflow can run on GPUs, you might be wondering why we might want to run
it on slower CPUs? One reason is that CPUs are plentiful while GPUs are still
somewhat scarce. If you have a lot of shorter Tensorflow jobs, they might
complete faster on available CPUs, rather than wait in the queue for the
faster, less available, GPUs. The good news is that Tensorflow code should
work in both enviroments automatically, so if your code runs too slow on CPUs,
moving to GPUs should be easy.

To submit our job, we need a submit file and a job wrapper script. The
submit file is an HTCondor file specifying that
we want the job to run in a container. Note `request_gpus = 0`, as we want
this job to use only CPU resources. The submit file, `cpu-job.submit`, is as follows:

    universe = vanilla

    # Job requirements - ensure we are running on a Singularity enabled
    # node and have enough resources to execute our code
    # Tensorflow also requires AVX instruction set and a newer host kernel
    Requirements = HAS_SINGULARITY == True && HAS_AVX2 == True && OSG_HOST_KERNEL_VERSION >= 31000
    request_cpus = 1
    request_gpus = 0
    request_memory = 1 GB
    request_disk = 1 GB

    # Container image to run the job in
    +SingularityImage = "/cvmfs/singularity.opensciencegrid.org/opensciencegrid/tensorflow:2.3"

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


The job wrapper script, `job-wrapper.sh`, contains the following lines:

    #!/bin/bash

    set -e

    echo
    echo "I'm running on" $(hostname -f)
    echo "OSG site: $OSG_SITE_NAME"
    echo

    python3 test.py 2>&1


The job can now be submitted with `condor_submit cpu-job.submit`. Once the job
is done, check the files named after the job id for the outputs. Where did your
job run? Based on the logs coming from `tensorflow` can you confirm that
the CPU was in fact used?


