<style type="text/css">.rendered-markdown{font-size:14px} .rendered-markdown>*:first-child{margin-top:0!important} .rendered-markdown>*:last-child{margin-bottom:0!important} .rendered-markdown a{text-decoration:underline;color:#b75246} .rendered-markdown a:hover{color:#f36050} .rendered-markdown h1, .rendered-markdown h2, .rendered-markdown h3, .rendered-markdown h4, .rendered-markdown h5, .rendered-markdown h6{margin:24px 0 10px;padding:0;font-weight:bold;-webkit-font-smoothing:antialiased;cursor:text;position:relative} .rendered-markdown h1 tt, .rendered-markdown h1 code, .rendered-markdown h2 tt, .rendered-markdown h2 code, .rendered-markdown h3 tt, .rendered-markdown h3 code, .rendered-markdown h4 tt, .rendered-markdown h4 code, .rendered-markdown h5 tt, .rendered-markdown h5 code, .rendered-markdown h6 tt, .rendered-markdown h6 code{font-size:inherit} .rendered-markdown h1{font-size:28px;color:#000} .rendered-markdown h2{font-size:22px;border-bottom:1px solid #ccc;color:#000} .rendered-markdown h3{font-size:18px} .rendered-markdown h4{font-size:16px} .rendered-markdown h5{font-size:14px} .rendered-markdown h6{color:#777;font-size:14px} .rendered-markdown p, .rendered-markdown blockquote, .rendered-markdown ul, .rendered-markdown ol, .rendered-markdown dl, .rendered-markdown table, .rendered-markdown pre{margin:15px 0} .rendered-markdown hr{border:0 none;color:#ccc;height:4px;padding:0} .rendered-markdown>h2:first-child, .rendered-markdown>h1:first-child, .rendered-markdown>h1:first-child+h2, .rendered-markdown>h3:first-child, .rendered-markdown>h4:first-child, .rendered-markdown>h5:first-child, .rendered-markdown>h6:first-child{margin-top:0;padding-top:0} .rendered-markdown a:first-child h1, .rendered-markdown a:first-child h2, .rendered-markdown a:first-child h3, .rendered-markdown a:first-child h4, .rendered-markdown a:first-child h5, .rendered-markdown a:first-child h6{margin-top:0;padding-top:0} .rendered-markdown h1+p, .rendered-markdown h2+p, .rendered-markdown h3+p, .rendered-markdown h4+p, .rendered-markdown h5+p, .rendered-markdown h6+p{margin-top:0} .rendered-markdown ul, .rendered-markdown ol{padding-left:30px} .rendered-markdown ul li>:first-child, .rendered-markdown ul li ul:first-of-type, .rendered-markdown ol li>:first-child, .rendered-markdown ol li ul:first-of-type{margin-top:0} .rendered-markdown ul ul, .rendered-markdown ul ol, .rendered-markdown ol ol, .rendered-markdown ol ul{margin-bottom:0} .rendered-markdown dl{padding:0} .rendered-markdown dl dt{font-size:14px;font-weight:bold;font-style:italic;padding:0;margin:15px 0 5px} .rendered-markdown dl dt:first-child{padding:0} .rendered-markdown dl dt>:first-child{margin-top:0} .rendered-markdown dl dt>:last-child{margin-bottom:0} .rendered-markdown dl dd{margin:0 0 15px;padding:0 15px} .rendered-markdown dl dd>:first-child{margin-top:0} .rendered-markdown dl dd>:last-child{margin-bottom:0} .rendered-markdown blockquote{border-left:4px solid #DDD;padding:0 15px;color:#777} .rendered-markdown blockquote>:first-child{margin-top:0} .rendered-markdown blockquote>:last-child{margin-bottom:0} .rendered-markdown table th{font-weight:bold} .rendered-markdown table th, .rendered-markdown table td{border:1px solid #ccc;padding:6px 13px} .rendered-markdown table tr{border-top:1px solid #ccc;background-color:#fff} .rendered-markdown table tr:nth-child(2n){background-color:#f8f8f8} .rendered-markdown img{max-width:100%;-moz-box-sizing:border-box;box-sizing:border-box} .rendered-markdown code, .rendered-markdown tt{margin:0 2px;padding:0 5px;border:1px solid #eaeaea;background-color:#f8f8f8;border-radius:3px} .rendered-markdown code{white-space:nowrap} .rendered-markdown pre>code{margin:0;padding:0;white-space:pre;border:0;background:transparent} .rendered-markdown .highlight pre, .rendered-markdown pre{background-color:#f8f8f8;border:1px solid #ccc;font-size:13px;line-height:19px;overflow:auto;padding:6px 10px;border-radius:3px} .rendered-markdown pre code, .rendered-markdown pre tt{margin:0;padding:0;background-color:transparent;border:0}</style>
<div class="rendered-markdown"><h2>Quash: A Simple Shell Implementation</h2>
<h2>Project Overview</h2>
<p>Quash (Quick Shell) is a simple command-line shell that replicates the core functionalities
<br  />of popular UNIX shells like sh, bash, csh, and tcsh. The goal of this project is to develop
<br  />a deeper understanding of command-line interfaces (CLI), process forking, background processes,
<br  />signal handling, I/O redirection, and piping.</p>
<h2>This shell was implemented in multiple tasks to incrementally add features:</h2>
<p>Task 1: Basic built-in commands (cd, pwd, echo, env, setenv, exit).
<br  />Task 2: Process creation and forking for external commands.
<br  />Task 3: Background process support using &amp;.
<br  />Task 4: Signal handling for Ctrl-C to avoid quitting the shell.
<br  />Task 5: Timer to kill long-running foreground processes after 10 seconds.
<br  />Task 6: I/O redirection with > and &lt; and piping with |.</p>
<h2>How to Use the Shell</h2>
<p>Compile the shell:
<br  />make</p>
<p>Run the shell:
<br  />./shell</p>
<p>Exit the shell by typing:
<br  />exit</p>
<h2>Built-in Commands</h2>
<p>cd <directory>: Change the current working directory.
<br  />pwd: Print the current working directory.
<br  />echo <message>: Print a message or environment variables (e.g., echo $PATH).
<br  />env: Display the list of environment variables.
<br  />setenv <VAR> <VALUE>: Set a new environment variable.
<br  />exit: Exit the shell.</p>
<h2>Features Implemented</h2>
<ol>
<li>Task 1: Built-in Commands
<br  />We implemented essential built-in commands such as cd, pwd, echo, env, setenv, and exit.
<br  />We tokenized user input to separate commands from arguments.</li>
<li>Task 2: Process Forking
<br  />We used fork() to create child processes and execvp() to execute external commands.
<br  />We handled errors for non-existent commands.</li>
<li>Task 3: Background Processes
<br  />We implemented background process support using &amp;.
<br  />The shell returns immediately to the prompt when a command is run in the background.</li>
<li>Task 4: Signal Handling
<br  />We implemented SIGINT (Ctrl-C) handling to prevent the shell from exiting.
<br  />The shell catches Ctrl-C and returns to the prompt without quitting.</li>
<li>Task 5: Killing Long-Running Processes
<br  />We used alarm() to set a 10-second timeout for foreground processes.
<br  />If a process exceeds the timeout, it is killed using kill().</li>
<li>Task 6: I/O Redirection and Piping
<br  />I/O Redirection:<blockquote><p>'>' redirects command output to a file.
<br  />Example:
<br  />cat shell.c > output.txt</p>
</blockquote>
</li>
</ol>
<blockquote><p>'<' redirects a file as input to a command.
<br  />Example:
<br  />more &lt; shell.c</p>
</blockquote>
<p>Piping:</p>
<blockquote><p>Pipes the output of one command as input to another.
<br  />Example:
<br  />cat testData | grep &ldquo;this&rdquo;</p>
</blockquote>
<h2>Design Choices</h2>
<p>Tokenization: We used strtok() to split user input into tokens.
<br  />Built-in Command Handling: we Checked if the user command was built-in before attempting to fork a new process.
<br  />Signal Handling: We implemented custom signal handlers for SIGINT and SIGALRM.
<br  />Redirection &amp; Piping: We used dup2() to redirect input/output streams and pipe() for piping between processes.</p>
<h2>Known Limitations and Future Improvements</h2>
<p>Command History: Currently, the shell does not store or display command history.
<br  />Job Control: Commands like fg, bg, and jobs are not implemented.
<br  />Enhanced Piping: Multiple piping (cmd1 | cmd2 | cmd3) could be added.</p>
<h2>Team Members</h2>
<p>Manoj Nath Yogi
<br  />Siddhartha Gautam</p>
<h2>Acknowledgements and References</h2>
<ol>
<li>Codio Instruction</li>
<li>Professor Legan Burge Lecture</li>
<li>Textbook: Used Chapter 3 as a reference for basic shell concepts.</li>
<li>Labs: Referenced Lab 3 - Part 1 for process forking and signal handling.</li>
<li>Linux Manual Pages: Used for understanding fork(), execvp(), signal(), dup2(), and wait() system calls.</li>
</ol>
</div>