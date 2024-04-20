# GNU Parallel

To execute arbitrary commands in parallel (multi-process), making use of additional CPU cores, across input data, [GNU `parallel`](https://www.gnu.org/software/parallel/) can be used.

A basic example is as follows:
```bash
find . -name '*.html' | parallel gzip --best
```
and more examples can be found [here](https://www.gnu.org/software/parallel/parallel_examples.html).