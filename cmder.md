
# cmder

### 修改提示符
C:\cmder\vendor\clink.lua

```
-- CG 
local cmder_prompt = "\x1b[1;32;40m{cwd}{git}{hg}{svn}>"
clink.prompt.value = string.gsub(cmder_prompt, "{cwd}", cwd)
```
### 修改aliases
C:\cmder\config\user_aliases.cmd

```
e.=explorer .

history=tail -n 200 "%CMDER_ROOT%\config\.history"
ll=ls -al --show-control-chars --color $*
enw=d: && cd d:\wisim\wisim.qt4
```
