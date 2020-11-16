By Kojiro

$1, $2, $3, ... are the positional parameters.

```bash
NAME=Tom
LASTNAME=Smith
/tmp/script.sh $NAME $LASTNAME
```

```bash
NAME=$1
LASTNAME=$2
echo "Hello, $NAME $LASTNAME"
```

"$@" is an array-like construct of all positional parameters, {$1, $2, $3 ...}.

"$*" is the IFS expansion of all positional parameters, $1 $2 $3 ....

$# is the number of positional parameters.

$- current options set for the shell.

$$ pid of the current shell (not subshell).

$_ most recent parameter (or the abs path of the command to start the current shell immediately after startup).

$IFS is the (input) field separator.

$? is the most recent foreground pipeline exit status.

$! is the PID of the most recent background command.

$0 is the name of the shell or shell script.


[source](https://stackoverflow.com/questions/5163144/what-are-the-special-dollar-sign-shell-variables)