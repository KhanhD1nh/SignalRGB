# SignalRGB

## Windows (PowerShell)

Chay lenh duoi day de tai `Components` va `Effects` tu repo, sau do copy vao thu muc `WhirlwindFX` trong `Documents` cua user hien tai (khong hard-code theo `C:\Users\Administrator\...`):

```powershell
$target = Join-Path $env:USERPROFILE "Documents\WhirlwindFX"
$temp = Join-Path $env:TEMP ("SignalRGB_" + [guid]::NewGuid().ToString())

git clone --depth 1 --filter=blob:none --sparse https://github.com/KhanhD1nh/SignalRGB.git $temp
git -C $temp sparse-checkout set Components Effects

New-Item -ItemType Directory -Force -Path $target | Out-Null
Copy-Item (Join-Path $temp "Components") -Destination $target -Recurse -Force
Copy-Item (Join-Path $temp "Effects") -Destination $target -Recurse -Force

Remove-Item $temp -Recurse -Force
```
