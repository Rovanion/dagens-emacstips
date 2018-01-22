1.  `git add -p`: Låter dig gå igenom diffen mot HEAD och avgöra bit
	för bit huruvida du vill schemalägga en bit kod för nästa commit.

	`git commit -p` finns även det för den som känner sig lite mera
	rakt på sak.

2.  `git commit -v`: Visar diffen du commit:ar under listan på filer i
	commitmeddelandestextfilen. Världens bästa flagga enligt utsago.

3.  `git show 8b8c70c`: Visar de förändringar som introducerades i
    commit `8b8c70c` som en diff. Användbart om du vill se vad var du
    gjorde i en specifik commit några steg tillbaka i tiden.

    `git show` utan argument visar diffen för commiten som `HEAD`
    hänvisar till, praktiskt att kolla just innan man kör `git push`
    för att se till att man inte får med något skräp.
