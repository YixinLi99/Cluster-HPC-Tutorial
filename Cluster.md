# Cluster Tutorial

In particular, SLURM: >https://curc.readthedocs.io/en/latest/compute/modules.html; >https://www.chpc.utah.edu/presentations/images-and-pdfs/SLURM-modules.pdf

Useful Training PPT：> http://depts.washington.edu/uwrcc/wordpress/wp-content/uploads/2020/10/HyakTrainingSession_F20_compressed.pdf

#### Bash Commands
To log in: 'ssh yixinli@159.226.64.67' password: 123456

To see the modules (apps): 'module avail'

To load the modules: ''' module load gaussian/g16.a03-avx                          
gaussian/g16.a03-avx2                         
gaussian/g16.a03-sse4_2  '''

To transfer files: 'scp', 'sftp', 'XShell'

#### Sample Slurm scripts 
```
#!/bin/bash
#SBATCH --job-name=gaussian      # create a short name for your job
#SBATCH --nodes=1                # node count
#SBATCH --ntasks=<N>             # total number of tasks across all nodes
#SBATCH --cpus-per-task=1        # cpu-cores per task (>1 if multi-threaded tasks)
#SBATCH --mem=40G                # total memory per node (4G per cpu-core is default)
#SBATCH --time=01:00:00          # total run time limit (HH:MM:SS)
#SBATCH --mail-type=begin        # send email when job begins
#SBATCH --mail-type=end          # send email when job ends
#SBATCH --mail-user=<YourNetID>@princeton.edu

module purge
module load gaussian/g16

g16 < input.com > output.log
```

```
vi ~/.bashrc
```
