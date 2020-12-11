# Rosalind-Tutorial

> https://rosalind.kcl.ac.uk/hpc/storage/

> https://www.geeksforgeeks.org/more-command-in-linux-with-examples/#:~:text=more%20command%20is%20used%20to,and%20down%20through%20the%20page.

###### Instructions: 

1. Download the two files from this email

2. Open your Rosalind account using the terminal
Move into your `scratch` directory (cd scratch, or cd sharedscratch)

3. Upload the files you have downloaded from your PC onto Rosalind. 

This could be tricky, it depends on how you have set up your account keys - so do get in touch if you struggle. For me I use the following:
on my laptop I open a terminal and type `cd Downloads`

Then I type `scp input.inp job_script.sh k1759875@login.rosalind.kcl.ac.uk:/path to my scratch directory`, then type my passwords. I find the `path to my scratch directory` by typing `pwd` in rosalind in my scratch directory

4. Run the job in Rosalind `sbatch job_script.sh`

6. Check the queue to ensure your job is running - `qstat k1763287`
When the job is running, practice using the `tail` and `more` commands to check the file as it updates

7. Try submitting the job again, asking for a different time or different number of nodes

###### Path to scratch direcotry Permission is Denied 

1. `ssh k1759875@login.rosalind.kcl.ac.uk`

2. enter passwords

3. `cd scratch`

4. `ls` (please tell me what you see when you write this command too)

5. `vi Test file`

6. `:wq` (to save the file and quit)

