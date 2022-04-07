# Cluster Tutorial

In particular, SLURM: > https://curc.readthedocs.io/en/latest/compute/modules.html; >https://www.chpc.utah.edu/presentations/images-and-pdfs/SLURM-modules.pdf

Useful Training PPT：> http://depts.washington.edu/uwrcc/wordpress/wp-content/uploads/2020/10/HyakTrainingSession_F20_compressed.pdf

<p align="center">
  <img src="https://user-images.githubusercontent.com/74641841/162175737-63348085-c189-4f19-aa04-60cb26a5e8a8.jpg" width="600" height="400"/>
</p>
#### Bash Commands
To log in: `ssh yixinli@159.226.64.67` password: 123456

To see the modules (apps): `module avail`

To load the modules: ```module load gaussian/g16.a03-avx                          
gaussian/g16.a03-avx2                         
gaussian/g16.a03-sse4_2```
if you forget the final several words, e.g. `module load multi...`, just click `tap`, the systerm will fill it for you.

To transfer files: `scp`, `sftp`, `XShell`

for `sftp`, just `sftp yixinli@159.226.64.67`, then you can type `put` to upload files onto slurm, and `get` to download files to local computer.

#### Sample Slurm scripts 
```
#!/bin/bash
#SBATCH --job-name=gaussian      # create a short name for your job
#SBATCH --nodes=1                # node count
#SBATCH --ntasks=<N>             # total number of tasks across all nodes
(#SBATCH --nodes=1 --ntasks-per-node=4)
#SBATCH --cpus-per-task=1        # cpu-cores per task (>1 if multi-threaded tasks)
#SBATCH --mem=40G                # total memory per node (4G per cpu-core is default)
#SBATCH --time=01:00:00          # total run time limit (HH:MM:SS)
#SBATCH --mail-type=begin        # send email when job begins
#SBATCH --mail-type=end          # send email when job ends
#SBATCH --mail-user=<YourNetID>@princeton.edu
#SBATCH -p X20Cv4
#SBATCH -J GAUSSIAN

module load gaussian/g16

g16 < input.com > output.log
```
For our cluster，scripts are pre-written. It is better to use them. 

To find them, `cd /home/scripts/SLURM/` generally. E.g. `/home/scripts/SLURM/g16` for gaussian 16. 

For GaussView on Cluster: `vi ~/.bashrc`  
To check the status of nodes: `cd /home/scripts/SLURM/g16` → `sinfo`: if its state is `alloc`, means you have to queque, choose the one with `idle` → `#SBATCH -p X20Cv4`, and the ntasks-per-node is determined by the number after X, e.g. `X16Cv3*`, then type `16*2` for ntasks-per-node. Notice that, `*` should not be included in the bash shell script, because it denotes it is the default one, when you didn't specify your used -p, you will use it.

To do the interactive commands, type `module load multiwfn/3.8-dev-almost-up-to-date`
for multiwfn and my molecule, `ulimit -s unlimited` is needed.
Then, `Multiwfn AQx.fch` and you will enter the interative UI of Multiwfn

If you want to logout from the cluster, type `logout`

Commands about your job： 
```
squeue: This gives a very long list of all jobs for all users. Bad if there are many jobs.
squeue -u <username>: This only shows your own jobs.
squeue -j <jobid>: Info just for a particular job. You get the jobid when you submit your job.
scontrol show job <jobid>: More information about a particular job, including a (rough) estimate of when the job starts.
```
`%NPRocShared=16` 调用16核parallel computation
`%Mem=32GB` 一共用最多32GB memory
X32Cv4 物理核心数+CPU版本
/opt/list_node_info.sh
ssh q2 /opt/list_node_info.sh 查看q2(node)的配置

