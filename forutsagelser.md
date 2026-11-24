# Förutsägelser: asynkron kod

Regler:

1. Titta på snutten i `snuttar/sNN.js` (eller på sidan `index.html`). **Kör den inte än.**
2. Skriv din gissning i tabellen: utskrifterna i den ordning du tror att de kommer, separerade med ` | `.
3. Kör snutten (knappen *Kör*). Skriv vad som faktiskt skrevs ut.
4. Hade du rätt? Skriv en regel med egna ord för varje snutt du gissade fel på.

| Snutt | Min gissning (i ordning) | Faktisk utskrift | Rätt? | Min regel om jag hade fel |
|:---:|---|---|:---:|---|
| 1 | skirver ut 1,2,3|1,2,3 |RÄTT | |
| 2 | ACB| ACB |RÄTT | |
| 3 |start,noll,kort,lång |s,n,k,l |RÄTT | |
| 4 |then:, inuti, klart,erfter | inuti, efter, then, klart | FEL!!| tänker att man börjar med con.log rad 8, och sdedan kommer promise con.log och så resolv slutligen conlog. Verkligen: Påbörjar promis [conlog], kör det som är kvar av skriptet dvs conlog rad 9, där efter hanteras rad 8 och på det resolven från promis |
| 5 | synk, promis, timeout| s,p,t |RÄTT | |
| 6 | F, 6,7| F,6,7 |Rätt | |
| 7 | f:,st| f:,st | RÄTT | |
| 8 | best, sät, bu, k| best, sätt, bull, kaff |RÄTT | |
| 9 | väntar, bulle, kaffe| v, [k,b]|FEL | startar prom, skriver ut cons.log(v). Där efter returnerar bulle, och sedan kaffe, och returnerar dem i nämnd ordning och skriver ut dem. Mitt mistag var att inte se att P.a använde [] och det ändrar resultatet. Då det inte skrivs ut förän hela arr är klar och ordningen i arr ändras inte |
| 10 | 1,6,2,3,4,5 |1,6,3,2,4,5 |FEL |Min tanke, c.l-1 och så c.l-6 där efter st-2 då timern är noll, där efter Promis-3 och slutligen st->där c.l-4 kommer före promis-5. Rätt är att P-3 kommer före st-2 då det är en timer som satts på kö och får ett kö# efter P-3 |
| 11 | c,a,b| c,ab|RÄTT | |

## Tre meningar med egna ord

1. JavaScript väntar inte på `setTimeout`, utan ger instansen ett 'könummer' och fortsätter tills man gått igenom hela koden och där efter kommer st i kö-ordning
2. En promise har tre tillstånd: then, catch, final
3. `then` körs alltid i fallande/skriven (uppifrån och ned) ordning under förutsättning att det inte kommer ett fel, då den som får felet inte körs utan felet hanteras av catch. Finaly körs efter att hela satsen är klar för att städa upp det hela.
