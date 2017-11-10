1.  `C-x C-SPC`: Hoppar till förra stället du var på i koden. T.ex. om
	du har sökt dig till ett ställe i koden för att hämta upp/kopiera
	någon bit information eller göra någon relaterad ändring kan du
	snabbt ta dig tillbaka igen.

2.  `C-x C-x`: Hoppar till punkten i koden du nyss var på, men byter
	plats på denna och utgångspunkten i minnet. Upprepade C-x C-x
	hoppar alltså fram och tillbaka mellan två punkter i koden.

	Bra för om man menade att markera det område mellan där en sökning
	utgick ifrån och där sökningen landade, men glömde det. Då kan man
	göra C-SPC C-x C-x och så har man markerat området.

3.  `C-s C-s` eller `C-r C-r`: Söker på det senast sökta sökordet
	igen.

4.  `C-s sökord C-g`: Går till nästa förekomst av sökord och sedan
	tillbaka utan att flytta markören. Bra för att kolla upp
	t.ex. tidigare användningar av en variabel för att sedan fortsätta
	skriva utan att behöva orientera sig i koden igen.

5.  `C-s söko C-w`: Kompletterar söktermen till slutet på ordet som
	pekaren står vid. Så har du börjat skriva in `söko` och pekaren
	därmed står likt `söko|rd` blir söktermen `sökord` när du trycker
	`C-w`.

	Kan användas som en fattig mans diff mellan två närliggande delar
	av en text, bara trycka ner `C-w` tills den andra delen inte
	längre matchar.
