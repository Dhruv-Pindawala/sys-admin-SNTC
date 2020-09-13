# Docker

## problem statement 1
Being a complete beginner in the field of docker or what most people call, NOOB, initially it was pretty tough for me to do problems related to docker but a co-community(telegram communtiy dedicted for pentesting related stuffs) member suugested me [Kode-Kloud]('https://kodekloud.com/courses/296044/lectures/11353782') which helped me a lot with this topic. This particular topic took a relly huge portion of the total time dedicated to this whole task/competition.
Other sources used by me: [Official node-js website]('https://nodejs.org/en/docs/guides/nodejs-docker-webapp/'), [edureka]('https://www.edureka.co/blog/what-is-docker-container') and [official docker documentation]('https://docs.docker.com/')
What I learnt?
A pretty straight forward answer to this question is that now I am confident with docker. Majority of basic topics are covvered by the sources mentioned above.
Image link : [dhhruv12/baat-cheet]('https://hub.docker.com/repository/docker/dhhruv12/baat-cheet')

## problem statement 2
My choice: Option 1
I would create a new user for him and grant him mininum privileges suing which he can run his project.
#### Execution
The primary command would be: [`sudo adduser limiteduser --shell=/bin/false --no-create-home`], here, limiteduser is the name of the user we created.
[`--no-create-home`] will skip creating a home directory for the user whereas [`--shell=/bin/false`] will make sure that the user will never get a shell access, no matter if they're trying to login locally or connect remotely using ssh.
Limitimg them in [`/etc/ssh/sshd_config`]: [`Matchuser user limiteduser`] [`ForceCommand /bin/false`], both these statements are in different lines of the file.
Giving enough permissions to run the ssh tunneling: [`ssh -N -D 1080 limiteduser@<server_ip_address>`], it connects successfully and establihes a tunnel between the user and the server which you can use to route your traffic at port 1080, and the best part is, wthe user don't even require a shhell access.
In case the limiteduser decides to ssh normally, they will get an error and ssh connection closes immediately.
In this way, we will secure thhe server from getting messed up. It will be of no/minimum use for the hacker or attacker even if they get the credentials of limiteduser.
In case, the user requires any extra permission, he would be granted it based on the server architecture and after verifing if the permission we are going give can,t be lethal to our server in any way.

## problem statement 3
Command : [`docker run -v /var/www/my-website:/usr/local/apache2/htdocs httpd`]
In the above command, var/www/my-website is the location of the directory that contains all the files related to the website. You can replace it with the location where all the website related files are saved on the host.
What i understood from docker volume is that docker container is just an instance of doocker image which means that all the data stored in a container is not permament and gets deleted once the container is exited. Docker volumes helpps us in this situation. It creates a volume simultaneously while the container is active so that even after the container is exited, it's data is not lost.