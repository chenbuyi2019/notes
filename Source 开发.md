# 软件下载
- [BSPSource](https://github.com/ata4/bspsrc/releases)
- [SteamCMD](https://developer.valvesoftware.com/wiki/SteamCMD)

# SteamCMD
```bash
login anonymous
app_update 740 validate #csgo服务端
app_update 4020 validate #gmod服务端
```

# Garry's Mod 对地图的限制
- MAX_MAP_ENTITIES - 8192 to 20480
- MAX_MAP_AREAS - 256 to 1024
- MAX_MAP_BRUSHES - 8192 to 16384
- MAX_NODES - 1500 to 4096
- Displacements - 2048 to 5500 
- MAX_MAP_MODELS - 4096
- MAX_MAP_OVERLAYS -512 to 1024
- MAX_MAP_BRUSHSIDES - 65k to 163k,  matching CS:GO limits

to 之前的数字表示原来的限制

# 编译脚本
```powershell
$ErrorActionPreference = "Stop"
$root = "C:\Program Files (x86)\Steam\steamapps\common\GarrysMod"
Set-Location "$root\bin"
$game = "$root\garrysmod"
$vmf = "C:\aaa.vmf"
$bsp = $vmf.Substring(0, $vmf.Length - 4) + ".bsp"
if (Test-Path -Path $bsp) {
    Remove-Item $bsp
}
$startTime = Get-Date
Write-Output "start VBSP : " $startTime.ToString()
./vbsp.exe -game $game -leaktest $vmf
if (Test-Path -Path $bsp) {
    Write-Output "start VVIS : " (Get-Date).ToString()
    ./vvis.exe -game $game $vmf
    Write-Output "start VRAD : " (Get-Date).ToString()
    ./vrad.exe -game $game $vmf
    Copy-Item -Path $bsp -Destination "$game\maps" -Force
}
Set-Location $PSScriptRoot
Write-Output "----"
$now = (Get-Date)
Write-Output ($now - $startTime)
Write-Output "----"
```
