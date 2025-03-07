Abbiamo già visto il Regex nell'ultima lezione
Su Linux, usiamo egrep per usare Regex
	`egrep $pattern $source`
`egrep` può prendere in input non una banale stringa ma una stringa che descrive una Regex
Se qualcosa matcha, ti ristampa la stringa con la parte matchata evidenziata

L'esempio dell'altra volta:
	`egrep -x "(0|1)*01"`
`-x` sta per *exact* e indica che l'intera stringa deve matchare
Eseguire quel comando ti fa entrare in una modalità dove ti valuta tutti gli input successivi
Senza `-x` cerca le sottostringhe

![[IMG_0858.png]]

L'opzione `-v` matcha ciò che non matcha l'espressione regolare fornita
	`egrep -v "00|11"`
Questa qui sopra matcha ciò che non contiene le sottostringhe 00 e 11

Caratteri speciali da ricordare:
	`^` - matcha l'inizio della riga
	`$` - matcha la fine della riga
	`.` - matcha qualunque carattere, una sola volta
	`\` - rimuove le funzioni speciali del prossimo carattere

Altri esempi:

Matcha solo se comincia con la maiuscola e poi ha solo lettere minuscole
Unit test:
	`Abba` sì
	`ciao` no
	`Ciao123` no
	`CiaoMamma` no
La regex che ci serve è `^[A-Z][a-z]+$`

Matcha sequenze di tre o più parole di solo lettere separate da esattamente uno spazio
Dopo l'ultima parola ci può essere uno spazio
Unit test:
	`qui quo qua` sì
	`qui quo qua ` sì
	`qui quo` no
	`qui quo qua3` no
	`qui quo       qua` no
La regex è `^([A-Za-z]+)( [A-Za-z]+)( [A-Za-z]+)*( )?$`
Per indicare che un `(`campo`)` va ripetuto esattamente N volte, fai `(){N}`