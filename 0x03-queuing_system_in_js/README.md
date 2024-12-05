String quoting and escaping
When redis-cli parses a command, whitespace characters automatically delimit the arguments. In interactive mode, a newline sends the command for parsing and execution. To input string values that contain whitespaces or non-printable characters, you can use quoted and escaped strings.

Quoted string values are enclosed in double (") or single (') quotation marks. Escape sequences are used to put nonprintable characters in character and string literals.

An escape sequence contains a backslash (\) symbol followed by one of the escape sequence characters.

Doubly-quoted strings support the following escape sequences:

\" - double-quote
\n - newline
\r - carriage return
\t - horizontal tab
\b - backspace
\a - alert
\\ - backslash
\xhh - any ASCII character represented by a hexadecimal number (hh)
Single quotes assume the string is literal, and allow only the following escape sequences:

\' - single quote
\\ - backslash
For example, to return Hello World on two lines:

127.0.0.1:6379> SET mykey "Hello\nWorld"
OK
127.0.0.1:6379> GET mykey
Hello
World
When you input strings that contain single or double quotes, as you might in passwords, for example, escape the string, like so:

127.0.0.1:6379> AUTH some_admin_user ">^8T>6Na{u|jp>+v\"55\@_;OU(OR]7mbAYGqsfyu48(j'%hQH7;v*f1H${*gD(Se'"
Host, port, password, and database
By default, redis-cli connects to the server at the address 127.0.0.1 with port 6379. You can change the port using several command line options. To specify a different host name or an IP address, use the -h option. In order to set a different port, use -p.

$ redis-cli -h redis15.localnet.org -p 6390 PING
PONG
If your instance is password protected, the -a <password> option will perform authentication saving the need of explicitly using the AUTH command:

$ redis-cli -a myUnguessablePazzzzzword123 PING
PONG
NOTE: For security reasons, provide the password to redis-cli automatically via the REDISCLI_AUTH environment variable.

Finally, it's possible to send a command that operates on a database number other than the default number zero by using the -n <dbnum> option:
