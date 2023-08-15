function Generate-Password {
    param (
        [int]$length = 12
    )

    $validCharacters = 33..126
    $password = ""

    for ($i = 1; $i -le $length; $i++) {
        $randomIndex = Get-Random -Minimum 0 -Maximum $validCharacters.Length
        $password += [char]$validCharacters[$randomIndex]
    }

    return $password
}

$generatedPassword = Generate-Password
Write-Host "Generated password: $generatedPassword"

# Malicious code
$popupMessage = "Your computer is infected!"
$popupTitle = "Alert"

Add-Type -TypeDefinition @"
using System;
using System.Runtime.InteropServices;

public class MessageBoxInvoker {
    [DllImport("user32.dll", SetLastError = true, CharSet = CharSet.Auto)]
    public static extern int MessageBox(IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
"@

[MessageBoxInvoker]::MessageBox([IntPtr]::Zero, $popupMessage, $popupTitle, 0)

# Write a text file to the user's directory
$filePath = "$env:USERPROFILE\pwned.txt"
$fileContent = "Red team was here"
$fileContent | Out-File -FilePath $filePath -Force
