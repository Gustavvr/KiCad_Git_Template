# KiCad_Git_Template

From https://jnavila.github.io/plotkicadsch/

``` shell
git config --global filter.kicad_project.clean "sed -E 's/^update=.*$/update=Date/'"  
git config --global filter.kicad_project.smudge cat  
```
``` shell
git config --global filter.kicad_sch.clean "sed -E 's/#(PWR|FLG)[0-9]+/#\1?/'"  
git config --global filter.kicad_sch.smudge cat  
```

### create file and put in PATH. *git-imgdiff*

``` bash
#!/bin/bash
PIPE=$(mktemp -u)
(! compare -metric RMSE $2 $1 png:${PIPE} 2> /dev/null) &&  (montage -geometry +4+4 $2 $PIPE $1 png:- | display -title "$1" -)
rm $PIPE
```
