#e http://artii.herokuapp.com/ is not longer online, but you can have an Idea on how to use it

# HappyBirthday
```` Ruby
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

$max      = [System.ConsoleColor].GetFields().Count - 1
$FontText = 
    "sketch_s",
    "com_sen_",
    "utopia",
    "sketch_s",
    "ticks",
    "xcourbi",
    "mirror",
    "xtimes",
    "lcd",
    "bigchief",
    "larry3d",
    "bulbhead",
    "jazmine",
    "broadway",
    "doom",
    "dotmatrix",
    "stellar",
    "speed",
    "os2",
    "pebbles",
    "shadow",
    "panther_",
    "rci_____"


for ($i = 0; $i -le 1; $i++){
    foreach ($Beep in $BeepList){
        [System.Console]::Beep($Beep['Pitch'], $Beep['Length'])
        #Write-Host -ForegroundColor $([System.ConsoleColor](Get-Random -Min 0 -Max $max)) "Happy Birthday"    ###Do this is Offline and remark the below

        $Font         = $(Get-Random -InputObject $FontText) #for a full listings https://artii.herokuapp.com/fonts_list
        $TextToEncode = [uri]::EscapeDataString("Happy Birthday!")
        $url          = "http://artii.herokuapp.com/make?text=$TextToEncode&font=$Font"
        $ouput        = Invoke-Restmethod -Uri $url -DisableKeepAlive -ErrorAction Stop
        Write-Host    -ForegroundColor $([System.ConsoleColor](Get-Random -Min 0 -Max $max)) $ouput -BackgroundColor Black
    }
}
````

#I took some audio code help from: https://www.reddit.com/r/PowerShell/comments/n5j3ic/happy_birthday_song_with_beep_tones_in_powershell/
