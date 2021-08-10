# OSG Virtual School Materials

## School Overview and Intro to HTC

View the slides
([PDF](files/osgvsp21-overview.pdf),
[PowerPoint](files/osgvsp21-overview.pptx))

Watch the lecture recording
([Intro to the Virtual School, HTC, and OSG](https://www.youtube.com/watch?v=vpJPPjoQ3QU))

## Intro to HTCondor Job Execution

View the slides
([PDF](htcondor/files/osgvsp21-htc-htcondor.pdf),
[PowerPoint](htcondor/files/osgvsp21-htc-htcondor.pptx))

Watch the lecture recording
([HTC Job Excecution with HTCondor](https://youtu.be/9896xAhT4dY))

### Intro Exercises 1: Running and Viewing Simple Jobs (Strongly Recommended)

- [Exercise 1.1: Log in to the local submit machine and look around](htcondor/part1-ex1-login)
- [Exercise 1.2: Experiment with HTCondor commands](htcondor/part1-ex2-commands.md)
- [Exercise 1.3: Run jobs!](htcondor/part1-ex3-jobs.md)
- [Exercise 1.4: Read and interpret log files](htcondor/part1-ex4-logs.md)
- [Exercise 1.5: Determining Resource Needs](htcondor/part1-ex5-request.md)
- [Exercise 1.6: Remove jobs from the queue](htcondor/part1-ex6-remove.md)
- [Bonus Exercise 1.7: Compile and run some C code](htcondor/part1-ex7-compile.md)

### Intro Exercises 2: Running Many HTC Jobs (Strongly Recommended)

- [Exercise 2.1: Work with input and output files](htcondor/part2-ex1-files.md)
- [Exercise 2.2: Use `queue N`, `$(Cluster)`, and `$(Process)`](htcondor/part2-ex2-queue-n.md)
- [Exercise 2.3: Use `queue from` with custom variables](htcondor/part2-ex3-queue-from.md)
- [Bonus Exercise 2.4: Use `queue matching` with a custom variable](htcondor/part2-ex4-queue-matching.md)

### Bonus Exercises: Job Attributes and Handling

- [Bonus Exercise 3.1: Explore `condor_q`](htcondor/part3-ex1-queue.md)
- [Bonus Exercise 3.2: Explore `condor_status`](htcondor/part3-ex2-status.md)
- [Bonus Exercise 3.3: A job that needs retries](htcondor/part3-ex3-job-retry.md)


## OSG

View the slides
([PDF](osg/files/osgvs21-day3-osg.pdf),
[PowerPoint](osg/files/osgvs21-day3-osg.pptx))

Watch the lecture recording
([Introduction to OSG](https://youtu.be/MVZ8jGgiv4k))

### OSG Exercises 1: Comparing CHTC and OSG (Strongly Recommended)

- [Exercise 1.1: Refresher – submitting multiple jobs](osg/part1-ex1-submit-refresher.md)
- [Exercise 1.2: Log in to the OS Pool Access Point](osg/part1-ex2-login-scp.md)
- [Exercise 1.3: Running jobs in OSG](osg/part1-ex3-submit-osg.md)
- [Exercise 1.4: Hardware differences between CHTC and OSG](osg/part1-ex4-hardware-diffs.md)
- [Exercise 1.5: Software differences in OSG](osg/part1-ex5-software-diffs.md)

### OSG Exercise 2: Troubleshooting (Strongly Recommended)

This one could take longer.  It is good to work through, but give yourself some time.

- [Exercise 2.1: Troubleshooting HTCondor jobs](osg/part2-ex1-troubleshooting.md)


## Software

View the slides
([PDF](software/files/osgvs21-software.pdf),
[PowerPoint](software/files/osgvs21-software.pptx))

Watch the lecture recording
([Backpacking with Code: Software Portability for DHTC](https://youtu.be/xUeIQbVXOMQ))

### Software Exercises 1: Basic Software and Wrapper Script Use (Strongly Recommended)

- [Exercise 1.1: Work With Downloaded Software](software/part1-ex1-download.md)
- [Exercise 1.2: Use a Wrapper Script To Run Software](software/part1-ex2-wrapper.md)
- [Exercise 1.3: Using Arguments With Wrapper Scripts](software/part1-ex3-arguments.md)

### Software Exercises 2: Specific Software Examples (Pick One)

- [Exercise 2.1: Compiling and Running a Simple Code](software/part2-ex1-compiling.md)
- [Exercise 2.2: Compiling a Research Software](software/part2-ex2-prepackaged.md)
- [Exercise 2.3: Compiling Python and Running Jobs](software/part2-ex3-python.md)
- [Exercise 2.4: Compiling Matlab and Running Jobs](software/part2-ex4-matlab.md)
- [Exercise 2.5: Using Conda Environments (Beta)](software/part2-ex5-conda.md)

### Software Exercises 3: Using Containers in Jobs (Strongly Recommended)

- [Exercise 3.1: Using Software in a Singularity Container](software/part3-ex1-singularity.md)

### Bonus Exercises: Container Examples

- [Exercise 4.1: Singularity Examples on OSG Connect](software/part4-ex1-singularity-options.md)
- [Exercise 4.2: Using Software in a Docker Container](software/part4-ex2-docker.md)
- [Exercise 4.3: Building Your Own Docker Container (Beta)](software/part4-ex3-docker-build.md)

## Data

View the slides
([PDF](data/files/osgvs21-data.pdf),
[PowerPoint](data/files/osgvs21-data.pptx))

Watch the lecture recording
([Handling Data on OSG](https://youtu.be/YBGWycYZRD4))

### Data Exercises 1: HTCondor File Transfer (Strongly Recommended)

- [Exercise 1.1: Understanding a job's data needs](data/part1-ex1-data-needs.md)
- [Exercise 1.2: Using data compression with HTCondor file transfer](data/part1-ex2-file-transfer.md)
- [Exercise 1.3: Splitting input](data/part1-ex3-blast-split.md)

### Data Exercises 2: Using Stash (Strongly Recommended)

- [Exercise 2.1: Using a web proxy for shared input](data/part2-ex1-blast-proxy.md)
- [Exercise 2.2: Stash for shared input](data/part2-ex2-stash-shared.md)
- [Exercise 2.3: Stash for shared output](data/part2-ex3-stash-unique.md)

### Bonus Exercises: Shared File Systems

- [Exercise 3.1: Shared filesystems for large input](data/part3-ex1-input.md)
- [Exercise 3.2: Shared filesystems for large output](data/part3-ex2-output.md)

## Extra Topics

### Self-checkpointing for long-running jobs

View the slides
([PDF](checkpoint/files/osgvs21-day6-checkpointing.pdf),
[PowerPoint](checkpoint/files/osgvs21-day6-checkpointing.pptx))

- [Exercise 1.1: Trying out self-checkpointing](checkpoint/part1-ex1-checkpointing.md)

### Containers and GPUs

View the slides
([PDF](gpus/files/osgvsp21-gpus-containers.pdf),
[PowerPoint](gpus/files/osgvsp21-gpus-containers.pptx))

- [Exercise 1.1: Containers Overview](gpus/part1-ex1-containers-overview.md)
- [Exercise 1.2: Running a CPU job](gpus/part1-ex2-cpu-jobs.md)
- [Exercise 1.3: Running a GPU job](gpus/part1-ex3-gpu-jobs.md)

### Introduction to Research Computing Facilitation

View the slides
([PDF](facilitation/files/osgvs21-htc-facilitation.pdf))

### Workflows with DAGMan

([PDF](workflows/files/osgvs21-bonus-dagman.pdf),
[PowerPoint](workflows/files/osgvs21-bonus-dagman.pptx))

- [Exercise 1.1: Coordinating set of jobs: A simple DAG](workflows/part1-ex1-simple-dag.md)
- [Exercise 1.2: A brief detour through the Mandelbrot set](workflows/part1-ex2-mandelbrot.md)
- [Exercise 1.3: A more complex DAG](workflows/part1-ex3-complex-dag.md)
- [Exercise 1.4: Handling jobs that fail with DAGMan](workflows/part1-ex4-failed-dag.md)
- [Bonus Exercise 4.5: HTCondor challenges](workflows/part1-ex5-challenges.md)
