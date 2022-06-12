# CP222_CSDFE
CIVE CP222 OpenSource Group work
# Sequence of Process creation
# 1. Init is created explicity by the kernel
# 2. Init will fork new process 'getty'
# 3. Exec getty the program responsible for configuring the tty with the loggin name & then envoking the login command
##>> When user enters username on the terminal getty will exec the login program
# 4. Upon successfull login the login progam will exec the user's shell.
# 5. Shell will then forks new process & exec the given command
# 6. When shell exits the init will reap the process fork again & exec getty on the available terminal once more

//NB: During the the login process there are number of files in the system that may be read and displayed to user,
//Such example of file is 'etcmotd' allowing administrator to display important messages to all users at login time

#kernel => init(8) #explicit creation
//init PID 1, PPID 0, EUID 0
#init(8) => getty(8) #fork(2) + exec(3)
//getty(8) PID N, PPID 1, EUID 0
#getty(8) => login(1) #exec(3)
//login(1) PID N, PPID 1, EUID 0
login(1) => $SHELL #exec(3)
//$SHELL PID N, PPID 1, EUID U
$SHELL => ls(1) #fork(2) + exec(3) 
//ls(1) PID M, PPID N, EUID U
//login file location in fs/nfsd/auth.c


/*To check git status */ git status
/*To congigure global usename and email*/ 
//git config --global user.name "username"
//git config --global user.email "youremail"
/*To check if email and username is configured type*/
// git config --list
/*To commit changed u must type */
//git commit -a -m "comment" where -a= all and -m = comment
/* To check the commit logs */
//git log 
//also u can specify number of log 
//git log -4
