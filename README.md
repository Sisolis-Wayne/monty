## 0x18. C - Stacks, Queues - LIFO, FIFO
  <h4 class="task">
    0. push, pall
      <span class="alert alert-warning mandatory-optional">
        mandatory
      </span>
  </h4>


  <!-- Progress vs Score -->

<!-- Task Body -->
  <p>Implement the <code>push</code> and <code>pall</code> opcodes.</p>

<p><strong>Monty byte code files</strong></p>

<p>Files containing Monty byte codes usually have the <code>.m</code> extension. Most of the industry uses this standard but it is not required by the specification of the language.
There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument:</p>

<pre><code>julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ cat -e bytecodes/000.m
push 0$
push 1$
push 2$
  push 3$
                   pall    $
push 4$
    push 5    $
      push    6        $
pall$
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$
</code></pre>

<p>Monty byte code files can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:</p>

<pre><code>julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ cat -e bytecodes/001.m
push 0 Push 0 onto the stack$
push 1 Push 1 onto the stack$
$
push 2$
  push 3$
                   pall    $
$
$
                           $
push 4$
$
    push 5    $
      push    6        $
$
pall This is the end of our program. Monty is awesome!$
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$
</code></pre>

<p><strong>The monty program</strong></p>

<ul>
<li>Usage: <code>monty file</code></li>
<li>where <code>file</code> is the path to the file containing Monty byte code</li>
<li>If the user does not give any file or more than one argument to your program, print <code>USAGE: monty file</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code></li>
<li>If, for any reason, it&#39;s not possible to use read the file, print <code>Error: Can&#39;t open file &lt;file&gt;</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code>

<ul>
<li>where <code>&lt;file&gt;</code> is the name of the file</li>
</ul></li>
<li>If the file contains an invalid instruction, print <code>L&lt;line_number&gt;: unknown instruction &lt;opcode&gt;</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code>

<ul>
<li>where <line_number> is the line number where the instruction appears. Line numbers always start at 1</li>
</ul></li>
<li>The monty program runs the bytecodes line by line and stop if:

<ul>
<li>it executed properly every line of the file</li>
<li>or it finds an error in the file</li>
<li>or an error occured</li>
</ul></li>
<li>If you can&#39;t malloc anymore, print <code>Error: malloc failed</code>, followed by a new line, and exit with status <code>EXIT_FAILURE</code>. You have to use <code>malloc</code> and <code>free</code> and are not allowed to use any other function from <code>man malloc</code></li>
</ul>

<p><strong>The push opcode</strong></p>

<p>The opcode <code>push</code> pushes an element to the stack.</p>

<ul>
<li>Usage: <code>push &lt;int&gt;</code></li>
<li>where <code>&lt;int&gt;</code> is an integer</li>
<li>if <code>&lt;int&gt;</code> is not an integer or if there is no argument to <code>push</code>, print the message <code>L&lt;line_number&gt;: usage: push integer</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code>

<ul>
<li>where <line_number> is the line number in the file</li>
</ul></li>
<li>You don&#39;t have to deal with overflows. Use the <code>atoi</code> function</li>
</ul>

<p><strong>The pall opcode</strong></p>

<p>The opcode <code>pall</code> prints all the values on the stack, starting from the top of the stack.</p>

<ul>
<li>Usage <code>pall</code></li>
<li>Format: see example</li>
<li>If the stack is empty, don&#39;t print anything</li>
</ul>

<pre><code>julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ cat -e bytecodes/00.m
push 1$
push 2$
push 3$
pall$
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ ./monty bytecodes/00.m
3
2
1
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$
</code></pre>

