
* Script console

Run command in script console, but capture stderr as well as stdout.

```groovy
def cmd = 'python -v'
def proc = cmd.execute()
proc.waitFor()
println "return code: ${ proc.exitValue()}"
println "stderr: ${proc.err.text}"
println "stdout: ${proc.in.text}"
```
