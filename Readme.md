 ```Java
 function convert-Font {
 #For this function source = https://github.com/kunaludapi although it has been modifed to fit this repro, as the API website is Offline
    [CmdletBinding(SupportsShouldProcess=$True,
        ConfirmImpact='Medium',
        HelpURI='http://vcloud-lab.com',
        DefaultParameterSetName='Inbuilt')]
    Param
    (
        [parameter(Position=0, ParameterSetName='Inbuilt', ValueFromPipelineByPropertyName=$true, ValueFromPipeline=$true, HelpMessage='Provide valid text')]
        [parameter(Position=0, ParameterSetName='Online', ValueFromPipelineByPropertyName=$true, ValueFromPipeline=$true, HelpMessage='Provide valid text')]
        [string]$Text = '# This is test !',
        [parameter(Position=2, ParameterSetName='Inbuilt', ValueFromPipelineByPropertyName=$true, HelpMessage='Provide existing font hight')]
        [Alias('Hight')]    
        [string]$FontHight = '5',
    
        [parameter(Position=1, ParameterSetName='Inbuilt', ValueFromPipelineByPropertyName=$true, ValueFromPipeline=$true, HelpMessage='Provide valid console color')]
        [parameter(ParameterSetName = 'Online', Position=1, Mandatory=$false, HelpMessage='Provide valid console color')]  
        [Alias('Color')]
        [ValidateSet('Black', 'DarkBlue','DarkGreen','DarkCyan', 'DarkRed','DarkMagenta','DarkYellow','Gray','DarkGray','Blue','Green','Cyan','Red','Magenta','Yellow','White')]
        [string]$FontColor = 'Yellow'
    )
    Begin {
        #$NonExistFont = $null
        if ($PsCmdlet.ParameterSetName -eq 'Inbuilt') {
            $a = {<#a 07#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#a#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor  -NoNewline; Write-Host " "
            <#a#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor  -NoNewline; Write-Host " "
            <#a#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#a#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor  -NoNewline; Write-Host " "} 
            $b = {<#b 07#> Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 3) 
            <#b#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor   -NoNewline; Write-Host " "
            <#b#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#b#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor  -NoNewline; Write-Host " "
            <#b#> Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 3) } 
            $c = {<#c 07#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#c#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4) 
            <#c#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4)
            <#c#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4)
            <#c#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $d = {<#d 07#> Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 3)
            <#d#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#d#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#d#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#d#> Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 3)}  
            $e = {<#e 06#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#e#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4)
            <#e#> Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host "  " 
            <#e#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4)
            <#e#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $f = {<#f 07#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#f#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4)
            <#f#> Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host "  "
            <#f#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4)
            <#f#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4)}
            $g = {<#g 07#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#g#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 5)
            <#g#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host " " -NoNewline -BackgroundColor $FontColor; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#g#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#g#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $h = {<#h 07#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#h#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#h#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#h#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#h#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $i = {<#i 03#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#i#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "  
            <#i#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#i#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#i#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $j = {<#j 07#> Write-Host "  " -NoNewline; Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#j#> Write-Host $(" " * 4) -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host " "  
            <#j#> Write-Host $(" " * 4) -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host " " 
            <#h#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#j#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $k = {<#k 09#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#k#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host " " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)
            <#k#> Write-Host $(" " * 3) -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 5)
            <#k#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host " " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)
            <#k#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $l = {<#l 05#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host "  " -NoNewline; Write-Host " "
            <#l#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)
            <#l#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)
            <#l#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)
            <#l#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $m = {<#m 09#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#m#> Write-Host $(" " * 3) -NoNewline -BackgroundColor $FontColor; Write-Host "  " -NoNewline; Write-Host $(" " * 3) -NoNewline -BackgroundColor $FontColor; Write-Host " "
            <#m#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host " " -NoNewline ; Write-Host "  " -NoNewline -BackgroundColor $FontColor ; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#m#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#m#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $n = {<#n 09#> Write-Host $(" " * 3) -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#n#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host " " -NoNewline; Write-Host " " -NoNewline -BackgroundColor $FontColor; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#n#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host "  " -NoNewline; Write-Host " " -NoNewline -BackgroundColor $FontColor ; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#n#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3) -NoNewline; Write-Host " " -NoNewline -BackgroundColor $FontColor; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#n#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $o = {<#o 07#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#o#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#o#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#o#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#o#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $p = {<#p 07#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#p#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#p#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#p#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 5) 
            <#p#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 5)}
            $q = {<#q 09#> Write-Host "  " -NoNewline; Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 3)
            <#q#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#q#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#q#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)
            <#q#> Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $r = {<#r 07#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#r#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#r#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#r#> Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 3)
            <#r#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $s = {<#s 07#> Write-Host "  " -NoNewline; Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#s#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 5)
            <#s#> Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)
            <#s#> Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#s#> Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host " "}
            $t = {<#t 07#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#t#> Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)
            <#t#> Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)
            <#t#> Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3) 
            <#t#> Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)}
            $u = {<#u 07#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#u#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#u#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#u#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#u#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $v = {<#v 11#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 6) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#v#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 6) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#v#> Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  "
            <#v#> Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3)
            <#v#> Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 5)}
            $w = {<#W 09#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host  $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#W#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host  $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#W#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline ; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#W#> Write-Host $(" " * 3) -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host $(" " * 3) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#W#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host  $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $x = {<#x 09#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#x#> Write-Host " " -NoNewline ; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host "  " 
            <#x#> Write-Host $(" " * 3) -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 4) 
            <#x#> Write-Host " " -NoNewline ; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host "  " 
            <#x#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $y = {<#y 11#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#y#> Write-Host " " -NoNewline;  Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  "
            <#y#> Write-Host $(" " * 3) -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 4) 
            <#y#> Write-Host $(" " * 3) -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 4) 
            <#y#> Write-Host $(" " * 3) -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 4)}
            $z = {<#z 07#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#z#> Write-Host $(" " * 4) -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor ; Write-Host " " 
            <#z#> Write-Host "  " -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 3) 
            <#z#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 5)
            <#z#> Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $hyphen = {<#- 05#> Write-Host $(" " * 5)
            <#-#> Write-Host $(" " * 5)
            <#-#> Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#-#> Write-Host $(" " * 5)
            <#-#> Write-Host $(" " * 5)}
            $Hash = {<## 11#> Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host (" " * 3)
            <###> Write-Host $(" " * 10) -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <###> Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host (" " * 3)
            <###> Write-Host $(" " * 10) -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <###> Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host (" " * 3)}
            $AtRate = {<#@ 09#> Write-Host " " -NosNewline; Write-Host $(" " * 6) -BackgroundColor $FontColor -NoNewline; Write-Host "  "
            <#@#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host (" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#@#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host " " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#@#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  " -NoNewline; Write-Host " " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#@#> Write-Host " " -NoNewline; Write-Host $(" " * 4) -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline;  Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $Exlaim = {<#! 03#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#!#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "  
            <#!#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#!#> Write-Host $(" " * 3)
            <#!#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $Dot = {<#. 03#> Write-Host $(" " * 3)
            <#.#> Write-Host $(" " * 3)  
            <#.#> Write-Host $(" " * 3) 
            <#.#> Write-Host $(" " * 3)
            <#.#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $Forward = {<#. 07#> Write-Host $(" " * 4) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#/#> Write-Host $(" " * 3) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host "  "
            <#/#> Write-Host "  " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 3)
            <#/#> Write-Host $(" " * 1) -NoNewline ; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4)
            <#/#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 5)}
            $Colun = {<#: 03#> Write-Host $(" " * 3)
            <#:#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#:#> Write-Host $(" " * 3)  
            <#:#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#:#> Write-Host $(" " * 3)}
            $Space = {<#  02#> Write-Host $(" " * 2)
            <# #> Write-Host $(" " * 2)
            <# #> Write-Host $(" " * 2)
            <# #> Write-Host $(" " * 2)
            <# #> Write-Host $(" " * 2)}
            $1 = {<#1 04#> Write-Host $(" " * 3) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#1 #> Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#1 #> Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#1 #> Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#1 #> Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $2 = {<#2 06#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#2#> Write-Host $(" " * 3) -NoNewline; Write-Host "  " -NoNewline -BackgroundColor $FontColor ; Write-Host " " 
            <#z#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#z#> Write-Host "  " -NoNewline -BackgroundColor $FontColor; Write-Host $(" " * 4)
            <#z#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $3 = {<#3 06#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#3#> Write-Host $(" " * 3) -NoNewline;  Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#3#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#3#> Write-Host $(" " * 3) -NoNewline;  Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#3#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $4 = {<#4 06#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#4#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#4#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#4#> Write-Host $(" " * 3) -NoNewline;  Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#4#> Write-Host $(" " * 3) -NoNewline;  Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $5 = {<#5 06#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#s#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4)
            <#s#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#s#> Write-Host $(" " * 3) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#s#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $6 = {<#6 06#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#6#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host $(" " * 4)
            <#6#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#6#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#6#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $7 = {<#7 06#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#7#> Write-Host $(" " * 3) -NoNewline;  Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#7#> Write-Host $(" " * 3) -NoNewline;  Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#7#> Write-Host $(" " * 3) -NoNewline;  Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#7#> Write-Host $(" " * 3) -NoNewline;  Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $8 = {<#8 06#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#8#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#8#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#8#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#8#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $9 = {<#9 06#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#9#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#9#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "
            <#9#> Write-Host $(" " * 3) -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#9#> Write-Host $(" " * 5) -BackgroundColor $FontColor -NoNewline; Write-Host " "}
            $0 = {<#0 06#> Write-Host " " -NoNewline ;Write-Host $(" " * 3) -BackgroundColor $FontColor -NoNewline; Write-Host "  "
            <#0#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#0#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#0#> Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " -NoNewline; Write-Host "  " -BackgroundColor $FontColor -NoNewline; Write-Host " " 
            <#0#> Write-Host " " -NoNewline; Write-Host $(" " * 3) -BackgroundColor $FontColor -NoNewline; Write-Host "  "}
        }#if
    }
    Process {
        switch ($PsCmdlet.ParameterSetName) {
            'Inbuilt' {    
                [char[]]$AllCharacters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890'
                foreach ($singleChar in $AllCharacters) {
                    $CharScript = Get-Variable -Name $singleChar | Select-Object -ExpandProperty Value
                    $CharScript = ($CharScript -split "`r`n")
                    New-Variable -Name $singleChar -Value $CharScript -Force
                }
                $hyphen = $hyphen -split "`r`n"
                $Hash = $Hash -split "`r`n"
                $AtRate = $AtRate -split "`r`n"
                $Exlaim = $Exlaim -split "`r`n"
                $Dot = $Dot -split "`r`n"
                $Forward = $Forward -split "`r`n"
                $Colun = $Colun -split "`r`n"
                $Space = $Space -split "`r`n"

                $textlength = $text.Length 
                [char[]]$TextBreakDown = $text 
  
                $wordart = @() 
                $FindWidth  = @()
                $NonExistFont = @()

                for ($ind= 0; $ind -lt $FontHight; $ind++) { 
                    $Conf = 1 
                    foreach ($character in $TextBreakDown) { 
                        $NoFont = $True
                        Switch -regex ($character) {
                            '-' {
                                $charname =  Get-Variable -Name hyphen
                                break
                            } #-
                            '#' {
                                $charname =  Get-Variable -Name Hash
                                break
                            } ##
                            '@' {
                                $charname =  Get-Variable -Name AtRate
                                break
                            } #-
                            '!' {
                                $charname =  Get-Variable -Name Exlaim
                                break
                            } #!
                            '\.' {
                                $charname =  Get-Variable -Name Dot
                                break
                            } #.
                            ':' {
                                $charname =  Get-Variable -Name Colun
                                break
                            } #.
                            '/' {
                                $charname =  Get-Variable -Name Forward
                                break
                            } #.
                            '\s' {
                                $charname =  Get-Variable -Name space
                                break
                            } #.
                            "[A-Za-z_0-9]" {
                                $charname = Get-Variable -Name $character
                                break
                            } 
                            default {
                                $NoFont = $false
                                break
                            } #default
                        } #switch
                
                        if ($NoFont -eq $True) {
                            if ($Conf -eq $textlength) { 
                                $info = $charname.value[$ind] 
                                $wordart += $info
                            } #if conf
                            else {
                                $info = $charname.value[$ind] 
                                $wordart += "{0} {1}" -f $info, '-NoNewLine'
                            } #else conf
                            $wordart += "`r`n"
                
                            #Get First Line to calculate width
                            if ($ind -eq 0) {
                                $FindWidth += $charname.value[$ind]
                            } #if ind
                
                            #Calculate font width
                            if ($ind -eq 0) {
                                $AllFirstLines = @()
                                $FindWidth = $FindWidth.trim() | Where-Object {$_ -ne ""}
                                $CharWidth = $FindWidth | foreach {$_.Substring(4,2)}
                                $BigFontWidth = $CharWidth | Measure-Object -Sum | Select-Object -ExpandProperty Sum
                            } #if ind

                        } #if NoFont
                        else {
                            $NonExistFont += $character
                        } #else NoFont
                        $Conf++
                    } #foreach character
                } #for
                $TempFilePath = [System.IO.Path]::GetTempPath()
                $TempFileName = "{0}{1}" -f $TempFilePath, 'Show-BigFontOnConsole.ps1'
                $wordart | foreach {$_.trim()} | Out-File $TempFileName
                & $TempFileName
                if ($NonExistFont -ne $null) {
                    $NonExistFont = $NonExistFont | Sort-Object | Get-Unique
                    $NonResult = $NonExistFont -join " "
                    Write-Host "`n`nSkipping as, No ascii fonts found for $NonResult" -BackgroundColor DarkRed
                } # if NonExistFont
            } #Inbuilt
        } #switch pscmdlet
    }
    end {}
}

$BeepList = @(
    @{ Pitch = 1059.274; Length = 300; };
    @{ Pitch = 1059.274; Length = 200; };
    @{ Pitch = 1188.995; Length = 500; };
    @{ Pitch = 1059.274; Length = 500; };
    @{ Pitch = 1413.961; Length = 500; };
    @{ Pitch = 1334.601; Length = 950; };

    @{ Pitch = 1059.274; Length = 300; };
    @{ Pitch = 1059.274; Length = 200; };
    @{ Pitch = 1188.995; Length = 500; };
    @{ Pitch = 1059.274; Length = 500; };
    @{ Pitch = 1587.117; Length = 500; };
    @{ Pitch = 1413.961; Length = 950; };

    @{ Pitch = 1059.274; Length = 300; };
    @{ Pitch = 1059.274; Length = 200; };
    @{ Pitch = 2118.547; Length = 500; };
    @{ Pitch = 1781.479; Length = 500; };
    @{ Pitch = 1413.961; Length = 500; };
    @{ Pitch = 1334.601; Length = 500; };
    @{ Pitch = 1188.995; Length = 500; };
    @{ Pitch = 1887.411; Length = 300; };
    @{ Pitch = 1887.411; Length = 200; };
    @{ Pitch = 1781.479; Length = 500; };
    @{ Pitch = 1413.961; Length = 500; };
    @{ Pitch = 1587.117; Length = 500; };
    @{ Pitch = 1413.961; Length = 900; };
)
$textToSpeach = "Happy Birthday"
$FontColorS = 'Black', 'DarkBlue','DarkGreen','DarkCyan', 'DarkRed','DarkMagenta','DarkYellow','Gray','DarkGray','Blue','Green','Cyan','Red','Magenta','Yellow','White'
for ($i = 0; $i -le 1; $i++){
    foreach ($Beep in $BeepList){
        [System.Console]::Beep($Beep['Pitch'], $Beep['Length'])
        $FontColor    = $(Get-Random -InputObject $FontColorS)
        $TextToEncode = [uri]::EscapeDataString("Happy Birthday!")
        convert-Font -Text $textToSpeach -FontColor $FontColor  
    }
}
Add-Type -AssemblyName System.speech
$speak = New-Object System.Speech.Synthesis.SpeechSynthesizer
$speak.Speak($textToSpeach)
$speak.Dispose()
```
