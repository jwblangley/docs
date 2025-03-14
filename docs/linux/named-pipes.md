# Named Pipes

* A named pipe can be used to communicate between processes.
* A named pipe can be created with the following:

    ```sh
    mkfifo
    ```

* It is important to note that writing to a named pipe will fail or at best hang unless something is also reading from the pipe
* Named pipes can be used to create circular communications between applications too. This can be used, for example, to allow a scripted agent to communicate with a prompt-like process.

    ```sh
    mkfifo fifo
    cat fifo | tee fifo
    ```

    In this example, the first process (`cat`) is reading from `fifo` and outputting to stdin. The second process (`tee`) is reading stdin and writing it to tty as well as back to `fifo`, closing the loop
    * Note that stdin/stdout may be buffered and interfere with this loop. To fix this, you can use `stdbuf -i0 -o0` as a prefix to the second process.
