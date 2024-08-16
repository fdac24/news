## Initial setup

1. GitHub
   * Sign up for [GitHub](https://github.com/) if not already signed
     up. Pick default (free plan).
   * [Create ssh key](https://help.github.com/articles/generating-ssh-keys/) and link it with GitHub:
     - Ensure that you've created an SSH key if you do not already have one. (`ed25519` keys are recommended)
     - Make sure your public SSH keys are added to your GitHub account and that you can use them to access git repos
     - Do Not Share Your Private Key, in any circumstance
   * [Fork](https://help.github.com/articles/fork-a-repo/) and create a [pull request](https://help.github.com/articles/using-pull-requests/) on [students repository](https://github.com/fdac24/students) so I
      can add you to the to the GitHub group for the course.
      
     - Start by [**forking** the students repository](https://github.com/fdac24/students)
     - Add your utk net id as NETID.md (click on '+' - add 
               new file next to the https://github.com/fdac19/students/ link)
     - Click on Create Pull Request (do not create NETID.md, but replace NETID by your netid in all lowercase, e.g. `bklein3.md` or `audris.md`)
    
     - If you receive a `Permission denied: publickey ` error, Add this to your ssh/config file:
       ```
       Host github.com
         IdentityFile ~/.ssh/[your ssh key file]
       ```
       note: Your SSH key file is the one that doesn't end in `.pub`
1. Familiarize yourself with GitHub workflow
   * Walk through [workflow](#workflow) 
    
## Typical workflow
1. To start, [**fork** the repository][forking] for the test project (found under [github.com/fdac24](https://github.com/fdac24))
1. [**Clone**][ref-clone] the repository to your computer.
1. View, create, and edit your files
1. [**commit**][ref-commit] changes to complete your solution.
1. [**Push**][ref-push]/sync the changes up to GitHub.
1. [Create a **pull request**][pull-request] on the original repository


Feedback will be given in the pull request, so please respond with
your thoughts and questions!  You are welcome to open the pull
request as the work is still in-progress if you are stuck and want
to ask a question – just mention `@audris` with the question to make
sure I know to look at it sooner.

## Initial setup: to be done on/by Aug 31

## Configuring ssh 
  * On linux/mac
     * create .ssh/config
    	1. create ~/.ssh/config or add to it:
        ```ssh
         host da3
            hostname da3.eecs.utk.edu
            port YOURPORT #from students/Ports.md
            user YOURNETID
            LocalForward 8888 127.0.0.1:8888
            # add a line similar to below if your SSH key is not automatically used:
            #IdentityFile ~/.ssh/id_rsa
            # these two lines are in case we need to re-create any docker containers
            # and/or reset your container if you break it:
            StrictHostKeyChecking no
            UserKnownHostsFile /dev/null
         ```

        1. place your private key in ~/.ssh/ on your client / local machine
        1. Make sure permissions are right
         ```
          chmod -R og-rwx ~/.ssh
         ```
        1. ssh da3
    * Or ssh directly 
      ```bash
      # example uses an RSA key, update all arguments accordingly
      ssh -pYOURPORT -L8888:localhost:8888 -i ~/.ssh/id_rsa yournetid@da3.eecs.utk.edu
      ```
  * Windows 10 has ubuntu subsystem: please use it and follow
  linux/mac instructions above. Also please avoid gitbash on Windows: its
  ssh seems to have problems. If it works for anyone, please create a
  pull request with instructions
https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_overview


  * Putty is an ssh client for earlier versions of windows, please avoid if you have Win10 or later
  * [Instructions on how to generate ssh key running windows](https://docs.joyent.com/public-cloud/getting-started/ssh-keys/generating-an-ssh-key-manually/manually-generating-your-ssh-key-in-windows) 

       1. How to generate key via putty
       1. ![generate the key via puttygen](https://github.com/fdac21/news/blob/master/PuttyGen.png "generate new key puttygen")

       1. Copy the key
       1. ![public ssh key from puttygen](https://github.com/fdac21/news/blob/master/puttykey.png "public ssh key from puttygen")

       1. Save the private key and use it in your putty ssh session
       1. Copy the public key (highlited in the image) to add to the yournetid.key 
       1. Now work on creating and saving session: start putty and go to connection/ssh/tunnels, enter source and destination and click *add*
       1. ![port forwarding](https://github.com/fdac21/news/blob/master/puttyport.png "select port forwarding")

       1. Go to  go to connection/ssh/Auth and browse for your private key
       1. ![authentication](https://github.com/fdac21/news/blob/master/puttyauth.png "select secret key that was saved above")
       1. Go to  go to session enter hostname and *YOUR PORT* from ports.md in fdac/students
       1. ![session](https://github.com/fdac21/news/blob/master/puttysession.png "start putty session")
       1. Don't forget to _save_ the session before clicking open  


<!-- Links -->
[docker]:http://www.eecs.utk.edu/resources/it/kb/docker
[deliberate-practice]:http://www.psy.fsu.edu/faculty/ericsson/ericsson.exp.perf.html
[pull-request]:https://help.github.com/articles/creating-a-pull-request
[create-repo]: https://help.github.com/articles/create-a-repo
[forking]: https://guides.github.com/activities/forking/
[ref-clone]: http://gitref.org/creating/#clone
[ref-commit]: http://gitref.org/basic/#commit
[ref-push]: http://gitref.org/remotes/#push
[pull-request]: https://help.github.com/articles/creating-a-pull-request
[raw]: https://raw.githubusercontent.com/education/guide/master/docs/forks.md
