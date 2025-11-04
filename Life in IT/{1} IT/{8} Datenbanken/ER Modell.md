#ER-Modell
# Allgemeines

ER-Modell steht für Entity Relationship Modell und es beschreibt den Aufbau einer Datenbank oder einfach gesagt einer Informationssammlung mit Zusammenhängenden Informationen. 

# Bauteile eines ER-Diagramms

Das Kernelement eines jeden ER-Diagramms sind die Entitäten diese kann man sich wie eine Liste mit Infos zu dieser Entität vorstellen. Zum Beispiel hat die Entität 'Person' mehrere Instanzen wie zum Beispiel *Tom* und *Max*.

Ein weiteres Element ist das Attribut jedes Attribut gehört irgendwo dazu es kann nicht alleine existieren, in den meisten Fällen gehört ein Attribut zu einer Entität. Ein solches Beispiel wäre die Entität Person mit dem 'Vornamen' *Tom*.

Das Letzte richtige Element ist die Beziehung die das ER-Modell zu dem macht was es ist. Die Beziehung liegt immer zwischen zwei Entitäten und beschreibt wie diese zusammengehören. Zum Beispiel könnte die Person in einer Stadt '*wohnen*'.

Zu einer Beziehung gehört auch immer eine Kardinalität also eine Angabe wie diese in Relation stehen. Als Erklärung selbiges Beispiel in einer Stadt wohnen viele Personen aber eine Person wohnt nur in einer Stadt (Hauptwohnsitz). Das heißt die Beziehung ist '*1 zu n*'. Das n steht immer da wo die vielen sind in diesem Beispiel wäre das die Person.

![[ER-Diagramm.png]]