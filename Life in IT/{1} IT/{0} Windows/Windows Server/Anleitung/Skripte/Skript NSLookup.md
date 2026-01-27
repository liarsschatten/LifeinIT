# Mit nslookup DNS überprüfen
```powershell
# Dieses Skript prüft die DNS-Auflösung mehrerer Servernamen

# Liste der Hostnamen es können beliebig viele Hostnamen eintragen, getrennt durch Kommata.
$hosts = @(
    "dc01",
    "dc02",
    "FS",
    "dc01.firma.local",
    "dc02.firma.local",
    "fs.firma.local"
)

# Schleife für jede Adresse
foreach ($host in $hosts) {
    Write-Host "`nÜberprüfe $host..." -ForegroundColor Yellow
    try {
        $result = nslookup $host 2>$null
        if ($LASTEXITCODE -eq 0) {
            Write-Host $result
        } else {
            Write-Host "Fehler: $host konnte nicht aufgelöst werden." -ForegroundColor Red
        }
    } catch {
        Write-Host "Fehler beim Ausführen von nslookup für $host." -ForegroundColor Red
    }
}

Write-Host "`nFertig!" -ForegroundColor Green


# foreach durchläuft alle Einträge in der Hostliste.

# nslookup $h ruft das Windows‑Tool auf, das die DNS‑Auflösung für den jeweiligen Host prüft.

# 2>$null blendet Fehlermeldungen aus.

# $LASTEXITCODE -eq 0 bedeutet, dass der Befehl erfolgreich war. Wenn ja, wird das Ergebnis angezeigt.

# Wenn nicht, wird eine Fehlermeldung in roter Schrift ausgegeben.
```
