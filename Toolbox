# Impordi vajalikud kogumid
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
Add-Type -AssemblyName System.ServiceProcess

# Loo põhivorm
$vorm = New-Object System.Windows.Forms.Form
$vorm.Text = "Toolbox"
$vorm.Size = New-Object System.Drawing.Size(700, 600)
$vorm.StartPosition = "CenterScreen"
$vorm.BackColor = [System.Drawing.Color]::WhiteSmoke

# Loo sakikorntroll
$sakkJuhtimine = New-Object System.Windows.Forms.TabControl
$sakkJuhtimine.Dock = "Fill"
$sakkJuhtimine.TabPages.Clear()

# Loo sakid
$lülitaLeht = New-Object System.Windows.Forms.TabPage
$lülitaLeht.Text = "Väljalülitamine"
$lülitaLeht.BackColor = [System.Drawing.ColorTranslator]::FromHtml("#B57EDC")

$appiAllalaadimineLeht = New-Object System.Windows.Forms.TabPage
$appiAllalaadimineLeht.Text = "Rakenduste allalaadimine"
$appiAllalaadimineLeht.BackColor = [System.Drawing.ColorTranslator]::FromHtml("#BAE1D3")

$taskKillerLeht = New-Object System.Windows.Forms.TabPage
$taskKillerLeht.Text = "Task Killer"
$taskKillerLeht.BackColor = [System.Drawing.ColorTranslator]::FromHtml("#FF5733")

$teenusteLeht = New-Object System.Windows.Forms.TabPage
$teenusteLeht.Text = "Teenused"
$teenusteLeht.BackColor = [System.Drawing.ColorTranslator]::FromHtml("#728FCE")

$cliLeht = New-Object System.Windows.Forms.TabPage
$cliLeht.Text = "CLI"
$cliLeht.BackColor = [System.Drawing.ColorTranslator]::FromHtml("#9E1B32")

# Lisa lehed sakile
$sakkJuhtimine.TabPages.Add($lülitaLeht)
$sakkJuhtimine.TabPages.Add($appiAllalaadimineLeht)
$sakkJuhtimine.TabPages.Add($taskKillerLeht)
$sakkJuhtimine.TabPages.Add($teenusteLeht)
$sakkJuhtimine.TabPages.Add($cliLeht)

# Loo juhtelemendid Task Killer lehele
$taskKillerSilt = New-Object System.Windows.Forms.Label
$taskKillerSilt.Text = "Sisestage taski nimi või PID:"
$taskKillerSilt.Location = New-Object System.Drawing.Point(10, 20)
$taskKillerSilt.Size = New-Object System.Drawing.Size(150, 20)

$taskKillerTekstiKast = New-Object System.Windows.Forms.TextBox
$taskKillerTekstiKast.Location = New-Object System.Drawing.Point(10, 40)
$taskKillerTekstiKast.Size = New-Object System.Drawing.Size(200, 20)

$taskKillerNupp = New-Object System.Windows.Forms.Button
$taskKillerNupp.Text = "Task Killer"
$taskKillerNupp.Location = New-Object System.Drawing.Point(10, 70)
$taskKillerNupp.Size = New-Object System.Drawing.Size(100, 30)
$taskKillerNupp.BackColor = [System.Drawing.Color]::LightGray

# Loo juhtelemendid Task Killer lehele
$taskKillerLeht.Controls.Add($taskKillerSilt)
$taskKillerLeht.Controls.Add($taskKillerTekstiKast)
$taskKillerLeht.Controls.Add($taskKillerNupp)

# Loo juhtelemendid teenuste lehele
$teenusteSilt = New-Object System.Windows.Forms.Label
$teenusteSilt.Text = "Valige teenus:"
$teenusteSilt.Location = New-Object System.Drawing.Point(10, 20)
$teenusteSilt.Size = New-Object System.Drawing.Size(200, 20)

$teenusteComboBox = New-Object System.Windows.Forms.ComboBox
$teenusteComboBox.Location = New-Object System.Drawing.Point(10, 50)
$teenusteComboBox.Size = New-Object System.Drawing.Size(200, 20)

# Hangi teenuste nimekiri
$teenused = Get-Service | Select-Object -ExpandProperty Name
$teenusteComboBox.Items.AddRange($teenused)

$staatuseSilt = New-Object System.Windows.Forms.Label
$staatuseSilt.Text = "Staatus:"
$staatuseSilt.Location = New-Object System.Drawing.Point(10, 80)
$staatuseSilt.Size = New-Object System.Drawing.Size(100, 20)

$staatuseVäärtuseSilt = New-Object System.Windows.Forms.Label
$staatuseVäärtuseSilt.Location = New-Object System.Drawing.Point(120, 80)
$staatuseVäärtuseSilt.Size = New-Object System.Drawing.Size(100, 20)

# Loo juhtelemendid teenuste lehele
$teenusteLeht.Controls.Add($teenusteSilt)
$teenusteLeht.Controls.Add($teenusteComboBox)
$teenusteLeht.Controls.Add($staatuseSilt)
$teenusteLeht.Controls.Add($staatuseVäärtuseSilt)

# Lisa sündmustekäsitleja teenuse valiku jaoks
$teenusteComboBox.Add_SelectedIndexChanged({
    $valitudTeenus = $teenusteComboBox.SelectedItem
    $teenuseStaatus = (Get-Service -Name $valitudTeenus).Status
    $staatuseVäärtuseSilt.Text = $teenuseStaatus
})

# Loo juhtelemendid rakenduste allalaadimise lehele
$rakendusteSilt = New-Object System.Windows.Forms.Label
$rakendusteSilt.Text = "Vali rakendus, mida alla laadida:"
$rakendusteSilt.Location = New-Object System.Drawing.Point(10, 20)
$rakendusteSilt.Size = New-Object System.Drawing.Size(200, 20)

$spotifyKastike = New-Object System.Windows.Forms.CheckBox
$spotifyKastike.Text = "Spotify"
$spotifyKastike.Location = New-Object System.Drawing.Point(10, 50)
$spotifyKastike.Size = New-Object System.Drawing.Size(150, 20)

$checkboxDiscord = New-Object System.Windows.Forms.CheckBox
$checkboxDiscord.Text = "Discord"
$checkboxDiscord.Location = New-Object System.Drawing.Point(10, 80)
$checkboxDiscord.Size = New-Object System.Drawing.Size(150, 20)

$checkboxSteam = New-Object System.Windows.Forms.CheckBox
$checkboxSteam.Text = "Steam"
$checkboxSteam.Location = New-Object System.Drawing.Point(10, 110)
$checkboxSteam.Size = New-Object System.Drawing.Size(150, 20)

$checkboxChrome = New-Object System.Windows.Forms.CheckBox
$checkboxChrome.Text = "Chrome"
$checkboxChrome.Location = New-Object System.Drawing.Point(10, 140)
$checkboxChrome.Size = New-Object System.Drawing.Size(150, 20)

$checkboxTeamspeak = New-Object System.Windows.Forms.CheckBox
$checkboxTeamspeak.Text = "TeamSpeak"
$checkboxTeamspeak.Location = New-Object System.Drawing.Point(10, 170)
$checkboxTeamspeak.Size = New-Object System.Drawing.Size(150, 20)

$downloadButton = New-Object System.Windows.Forms.Button
$downloadButton.Text = "Tõmba valitud"
$downloadButton.Location = New-Object System.Drawing.Point(10, 200)
$downloadButton.Size = New-Object System.Drawing.Size(150, 30)
$downloadButton.BackColor = [System.Drawing.Color]::LightGray

$downloadButton.Add_Click({
    if ($spotifyKastike.Checked) {
        Start-Process -FilePath "https://download.scdn.co/SpotifySetup.exe"
    }
    if ($checkboxDiscord.Checked) {
        Start-Process -FilePath "https://discord.com/api/download?platform=win"
    }
    if ($checkboxSteam.Checked) {
        Start-Process -FilePath "https://cdn.akamai.steamstatic.com/client/installer/SteamSetup.exe"
    }
    if ($checkboxChrome.Checked) {
        Start-Process -FilePath "https://dl.google.com/chrome/install/latest/chrome_installer.exe"
    }
    if ($checkboxTeamspeak.Checked) {
        Start-Process -FilePath "https://files.teamspeak-services.com/releases/client/3.5.6/TeamSpeak3-Client-win64-3.5.6.exe"
    }
    [System.Windows.Forms.MessageBox]::Show("Valitud rakendused tõmmatakse.", "Download", [System.Windows.Forms.MessageBoxButtons]::OK, [System.Windows.Forms.MessageBoxIcon]::Information)
})

# Lisa juhtelemendid rakenduste allalaadimise lehele
$appiAllalaadimineLeht.Controls.Add($rakendusteSilt)
$appiAllalaadimineLeht.Controls.Add($spotifyKastike)
$appiAllalaadimineLeht.Controls.Add($checkboxDiscord)
$appiAllalaadimineLeht.Controls.Add($checkboxSteam)
$appiAllalaadimineLeht.Controls.Add($checkboxChrome)
$appiAllalaadimineLeht.Controls.Add($checkboxTeamspeak)
$appiAllalaadimineLeht.Controls.Add($downloadButton)

# Loo juhtelemendid väljalülitamise valikute lehele
$lülitaSilt = New-Object System.Windows.Forms.Label
$lülitaSilt.Text = "Vali tegevus:"
$lülitaSilt.Location = New-Object System.Drawing.Point(10, 20)
$lülitaSilt.Size = New-Object System.Drawing.Size(200, 20)

$checkboxShutdown = New-Object System.Windows.Forms.CheckBox
$checkboxShutdown.Text = "Shutdown"
$checkboxShutdown.Location = New-Object System.Drawing.Point(10, 50)
$checkboxShutdown.Size = New-Object System.Drawing.Size(150, 20)

$checkboxReboot = New-Object System.Windows.Forms.CheckBox
$checkboxReboot.Text = "Reboot"
$checkboxReboot.Location = New-Object System.Drawing.Point(10, 80)
$checkboxReboot.Size = New-Object System.Drawing.Size(150, 20)

$checkboxLogout = New-Object System.Windows.Forms.CheckBox
$checkboxLogout.Text = "Logout"
$checkboxLogout.Location = New-Object System.Drawing.Point(10, 110)
$checkboxLogout.Size = New-Object System.Drawing.Size(150, 20)

$shutdownButton = New-Object System.Windows.Forms.Button
$shutdownButton.Text = "Execute"
$shutdownButton.Location = New-Object System.Drawing.Point(10, 140)
$shutdownButton.Size = New-Object System.Drawing.Size(150, 30)
$shutdownButton.BackColor = [System.Drawing.Color]::LightGray

$shutdownButton.Add_Click({
    if ($checkboxShutdown.Checked) {
        Stop-Computer
    }
    if ($checkboxReboot.Checked) {
        Restart-Computer
    }
    if ($checkboxLogout.Checked) {
        Shutdown.exe /l
    }
    [System.Windows.Forms.MessageBox]::Show("Valitud tegevus on lõpule viidud.", "Execution", [System.Windows.Forms.MessageBoxButtons]::OK, [System.Windows.Forms.MessageBoxIcon]::Information)
})

# Lisa juhtelemendid väljalülitamise valikute leheküljele
$lülitaLeht.Controls.Add($lülitaSilt)
$lülitaLeht.Controls.Add($checkboxShutdown)
$lülitaLeht.Controls.Add($checkboxReboot)
$lülitaLeht.Controls.Add($checkboxLogout)
$lülitaLeht.Controls.Add($shutdownButton)

# Lisa sakikontroll vormile
$cliSilt = New-Object System.Windows.Forms.Label
$cliSilt.Text = "Sisestage käsk:"
$cliSilt.Location = New-Object System.Drawing.Point(10, 20)
$cliSilt.Size = New-Object System.Drawing.Size(100, 20)

$cliTekstiKast = New-Object System.Windows.Forms.TextBox
$cliTekstiKast.Location = New-Object System.Drawing.Point(10, 50)
$cliTekstiKast.Size = New-Object System.Drawing.Size(300, 20)

$cliNupp = New-Object System.Windows.Forms.Button
$cliNupp.Text = "Käivita"
$cliNupp.Location = New-Object System.Drawing.Point(10, 80)
$cliNupp.Size = New-Object System.Drawing.Size(100, 30)
$cliNupp.BackColor = [System.Drawing.Color]::LightGray

$cliVäljund = New-Object System.Windows.Forms.TextBox
$cliVäljund.Location = New-Object System.Drawing.Point(10, 120)
$cliVäljund.Size = New-Object System.Drawing.Size(300, 200)
$cliVäljund.Multiline = $true
$cliVäljund.ScrollBars = "Vertical"

# Funktsioon, mis võimaldab käskude täitmist
$cliLeht.Controls.Add($cliSilt)
$cliLeht.Controls.Add($cliTekstiKast)
$cliLeht.Controls.Add($cliNupp)
$cliLeht.Controls.Add($cliVäljund)

$cliNupp.Add_Click({
    $käsk = $cliTekstiKast.Text
    $väljund = Invoke-Expression -Command $käsk
    $cliVäljund.Text = $väljund -join "`r`n"
})

$vorm.Controls.Add($sakkJuhtimine)

# Näitab vormi
[void]$vorm.ShowDialog()
