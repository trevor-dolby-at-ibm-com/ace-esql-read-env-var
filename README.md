# ace-esql-read-env-var
Example of reading environment variables from ESQL

## Code

Declaration in ESQL to enable access to the Java method:
```
CREATE FUNCTION javaLangSystemGetenv( IN name CHARACTER )
  RETURNS CHARACTER
  LANGUAGE JAVA
  EXTERNAL NAME "java.lang.System.getenv";
```

followed by using the Java function

```
    DECLARE pathValue CHARACTER;
    SET pathValue = javaLangSystemGetenv('PATH');
```        

## Example with ACE 11.0.0.18

```
tdolby@IBM-PF3K066L:~/workspace/WMB/src$ mqsicreateworkdir /tmp/ace-esql-read-env-var-work-dir
mqsicreateworkdir: Copying sample server.config.yaml to work directory
1 file(s) copied.
Successful command completion.
tdolby@IBM-PF3K066L:~/workspace/WMB/src$ mqsibar -c -w /tmp/ace-esql-read-env-var-work-dir -a /home/tdolby/git/ace-esql-read-env-var/ReadEnvVarApplication/ReadEnvVarApplication.bar
Generating runtime objects: '/tmp/ace-esql-read-env-var-work-dir/run' ...

BIP8071I: Successful command completion.
tdolby@IBM-PF3K066L:~/workspace/WMB/src$ IntegrationServer -w /tmp/ace-esql-read-env-var-work-dir --no-nodejs
.....2022-08-24 14:36:48.073280: .2022-08-24 09:36:48.073576: BIP1990I: Integration server 'ace-esql-read-env-var-work-dir' starting initialization; version '11.0.0.18' (64-bit)
.........................................2022-08-24 09:36:49.241360: BIP2155I: About to 'Initialize' the deployed resource 'ReadEnvVarApplication' of type 'Application'.
2022-08-24 09:36:49.362440: BIP2155I: About to 'Start' the deployed resource 'ReadEnvVarApplication' of type 'Application'.
2022-08-24 09:36:49.362632: BIP2269I: Deployed resource 'TimerFlow' (uuid='TimerFlow',type='MessageFlow') started successfully.
...
2022-08-24 09:36:49.362912: BIP1991I: Integration server has finished initialization.
2022-08-24 09:36:49.364256: BIP8099I: Read env var: PATH  -  /opt/ace-11.0.0.18/common/jdk/jre/bin:/var/mqsi/extensions/11.0.0/server/bin:/var/mqsi/extensions/11.0.0/bin:/opt/ace-11.0.0.18/server/bin:/opt/ace-11.0.0.18/common/node/bin:/opt/mqm/bin:/opt/ace-11.0.0.18/tools:/home/tdolby/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```
