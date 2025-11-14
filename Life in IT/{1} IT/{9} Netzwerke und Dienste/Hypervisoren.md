Hypervisors sind wie folgt zu verstehen, sie sind Systeme welche Betriebssysteme/Dienste verwalten und Ressourcen zuteilen sie sind essentiell für Server die mehrere Dienste anbieten sollen und User die mehrere Betriebssysteme nutzen.
Hypervisors sind in zwei verschiedene Typen zu unterteilen.
![[hypervisor.png]]
# Hypervisor Typ 1 - Bare Metal / Native Hypervisor
Ein Hypervisor Typ 1 setzt direkt auf der Hardware auf. Dieser Typ besteht lediglich aus der Software zur Verwaltung von Ressourcen. Er teilt den virtuellen Maschinen Ressourcen zu und verwaltet diese z.B. mit Checkpoints. Der Vorteil bei Typ 1 Hypervisors ist das sie sehr viel effizienter sind als Typ 2 weil sie direkt auf der Hardware aufsetzen und nicht auf ein Betriebssystem.
# Hypervisor Typ 2 - Hosted Hypervisor
Ein Hypervisor Typ 2 setzt nicht direkt auf der Hardware auf sondern auf einem Betriebssystem wie beispielsweise Windows oder Linux.
Es besitzt ähnliche Funktionen wie ein Typ 1 Hypervisor nur das noch ein Betriebssystem dazwischen geschaltet ist. Heißt im Endeffekt dass das Betriebssystem selbst auch noch Ressourcen nutzt und deshalb weniger Ressourcen für ein Virtuelle Maschine übrig sind. Ist dafür leichter aufzusetzen und benötigt keine Management Konsole