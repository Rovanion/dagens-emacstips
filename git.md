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

4.  Man kan definiera egna subkommandon till git som sedan opererar på
    t.ex. källkod en i förrådet. Jag har ett kommando psed som helt
    enkelt hittar alla förkomster av A och ersätter det med B om man
    kallar det likt `git psed A B`.

	Subkommandon definieras i `~/.gitconfig` under
    `[alias]`. Specifikt är `psed` definierat med raden:

	```
	psed = !sh -c 'git grep --null --full-name --name-only --perl-regexp -e \"$1\" | xargs -0 perl -i -p -e \"s/$1/$2/g\"' -
	```

	Ett annat kommando jag använder ofta är git lg, som git log fast
    visar bara sammanfattningarna och ritar en fin liten graf till
    vänster:

	```
	lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%C(bold blue)<%an>%Creset' --abbrev-commit
	```

5.  Vi känner alla till `git add --patch` som låter en välja vilka
    delar av en fil man ska förberedas för nästa commit. Denne har en
    mörk tvillingbror, `git reset --patch`, som låter dig göra det
    motsatta, d.v.s. ta bort en del av en fil som stod på kö för nästa
    commit.

	För att se vad som står köat för nästa commit kan du använda `git
    diff --cached`.

6.  Det går att ändra ordningen på commits när man kör `git rebase`.

	Detta kan till exempel komma till hands om du vill skapa en commit
    som är den näst senaste på din nuvarande gren. Låt säga din
    historik ser ut som följer:

	```
	* c2d3bd1 - (HEAD -> master) Stor funktion X.
    * ee8149f - Någon annan fin ändring som behövdes.
	```

	Det finns testsnurra som kör någonstans som sätts igång av att du
    trycker upp kod på gitserver. Så du har börjat ackumulera
    förändringar relaterat till X i nuvarande HEAD av master
    `c2d3bd1`. Men så finner du en till X orelaterad förändring som du
    vill göra, men kommer glömma bort om du inte gör den på
    direkten. Då skulle det vara fint att kunna lägga en commit mellan
    `ee8149f` och `c2d3bd1`.

	Detta gör lättast genom att du kör `git commit` som vanligt men
    sedan kör `git rebase HEAD~2 -i` och i din textbuffer sedan ändrar
    ordningen på `c2d3bd1` och din nyligen skapade commit så att den nya
    hamnar innan `c2d3bd1`.
