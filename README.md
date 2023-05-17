# PR22JKEVBMKLGSHJ

## ZARADI ČESA BOŠ UMRL, ČE ŽIVIŠ V SLOVENIJI?

## Projektna naloga – podatkovno rudarjenje
### Vmesno poročilo<br>

**Avtorji:** Jerneja Krajcar, Blaž Mikec, Katarina Levec Grajfoner, Samo Herksel Japelj, Eva Vidic<br>

Vsak se je že kdaj vprašal kako bo umrl, zato smo se mi odločili raziskati zaradi česa umirajo naši sokrajani. Ker vsak član naše ekipe prihaja iz svoje regije nas je zanimalo, če bo med nami prišlo do kakšnih razlik najverjetnejšega vzroka smrti. <br>

### Opis problema
Zanimajo nas najpogostejši vzroki smrti v Sloveniji in ali se razlikujejo glede na spol in regijo. Izbrali smo si podatke, ki nam prikažejo pogoste vzroke smrti v Sloveniji. S tem si lažje predstavljamo zdravstveno stanje celotnega prebivalstva in zaradi česa ljudje umrejo. Pogledali smo tudi ali je v času korone virusa število umrlih res naraslo.<br>

### Opis podatkov
Uporabljali bomo en vir podakov, z ministrstva za upravo in spadajo pod področje prebivalstva in družbe: https://podatki.gov.si/dataset/surs05l3016s. Podatki nudijo vpogled v pogoste vzroke smrti v Sloveniji, kar je ključno za razumevanje zdravstvenega stanja celotnega prebivalstva. Razdeljeni so na spol, statistično regijo, leto in vzrok smrti. Bolezni so opredeljene v šestih skupinah: nekatere infekcijske in parazitske bolezni, neoplazme, bolezni obtočil, bolezni dihal, bolezni prebavil ter poškodbe, zastrupitve in nekatere druge posledice zunanjih vzrokov. Meritve so opredeljene na enega ali tisoč prebivalcev. Podatki so tipa števec in obsegajo 10 920 podatkovnih polj. Število manjkajočih zapisov: manjkajo podatki za vzrok smrti nekatere infekcijske in parazitske bolezni do leta 2019.
Opis predprocesiranja: podatke smo naložili v obliki csv datoteke in s pomočjo ukaza read_csv shranili v podatkovno strukturo. <br>

### Glavna vprašanja/cilji
Naši cilj pri obdelavi podatkov in izdelavi grafov je bil odgovoriti na vprašanja:<br>
1.	Kateri vzrok smrti je najpogostejši glede na statistično regijo?
2.	Kateri vzrok smrti je najpogostejši za posamezen spol? 
3.	Kako je naraščalo število smrti po Sloveniji? 
4.	Kakšen je vpliv korone na število smrti med leti 2020 in 2022?
5.	Primerjava števila smrti z drugimi EU državami.

### Izvedene analize in glavne ugotovitve
Da bi odgovorili na vprašanja, ki smo si jih zadali, smo izdelali nekaj grafov:<br><br>
**1.	Kateri vzrok smrti je najpogostejši glede na statistično regijo?**<br>
* Največ ljudi (v vseh občinah) umre zaradi bolezni obtočil, drugi najpogostejši vzrok pa so infekcijske in parazitne bolezni.
* Najmanj ljudi (v vseh občinah) umre zaradi neoplazme.
* Pri skoraj vseh vzrokih je največ smrti v pomurski regiji.
* Najmanj smrti je v osrednjeslovenski regijii.

![Screenshot 2023-04-19 at 00 13 14](https://user-images.githubusercontent.com/61201874/232916631-56522e1c-0e37-442f-bc14-bde130b4d8b9.png)

Grafi vzrokov smrti po posameznih regijah:
![graf4](https://github.com/smoki599/PR22JKEVBMKLGSHJ/assets/79158550/1fcccbe6-5656-4360-b0cc-c3ff420d049c)
![graf5](https://github.com/smoki599/PR22JKEVBMKLGSHJ/assets/79158550/5afbadb7-b95b-4c6e-9a26-07a662eb15c9)

```
#==============SEZNAM VZROKOV=============

Y_old = df['STATISTIÈNA REGIJA'][1:13]

frame = pd.DataFrame(data=smrti, index = vzroki)

frame.plot( y=Y_old, kind='bar', figsize=(12,8), ylabel='Število smrti na 1000 prebivalcev"', rot=0)
frame.plot
plt.xlabel("Vzrok smrti")
plt.ylabel("Število smrti na 1000 prebivalcev")
plt.title("Vzrok smrti v regijah na 1000 prebivalcev")
plt.legend()
plt.xticks(rotation=90)
plt.show()

Y = odstraniSumnike(Y_old);


npFrame = frame.to_numpy();

Frame = pd.DataFrame(npFrame, index=vzroki, columns=Y).drop(vzroki[1:]).sort_values(by='Neoplazma', axis=1)
Frame.plot(kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0, color = returnColorOrder(Frame.columns))


Frame = pd.DataFrame(npFrame, index=vzroki, columns=Y).drop(returnAllBut(vzroki,1)[:]).sort_values(by='Infeciske in parazitne bolezni', axis=1)
Frame.plot(kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0, color = returnColorOrder(Frame.columns))

Frame = pd.DataFrame(npFrame, index=vzroki, columns=Y).drop(returnAllBut(vzroki,2)[:]).sort_values(by='Bolezni obtoèil', axis=1)
Frame.plot(kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0, color = returnColorOrder(Frame.columns))

Frame = pd.DataFrame(npFrame, index=vzroki, columns=Y).drop(returnAllBut(vzroki,3)[:]).sort_values(by='Bolezni dihal', axis=1)
Frame.plot(kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0,color = returnColorOrder(Frame.columns))

Frame = pd.DataFrame(npFrame, index=vzroki, columns=Y).drop(returnAllBut(vzroki,4)[:]).sort_values(by='Bolezni prebavil', axis=1)
Frame.plot(kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0, color = returnColorOrder(Frame.columns))

Frame = pd.DataFrame(npFrame, index=vzroki, columns=Y).drop(returnAllBut(vzroki,5)[:]).sort_values(by='Zunanji vzroki', axis=1)
Frame.plot(kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0, color = returnColorOrder(Frame.columns))

plt.show()
```
<br>


**2.	Kateri vzrok smrti je najpogostejši za posamezen spol?**<br>
* Pri ženskah so najpogostejši vzrok smrti bolezni obtočil, pri moških pa neoplazme.
* Najmanj moških in žensk umre zaradi bolezni prebavil.

![Screenshot 2023-04-19 at 00 15 57](https://user-images.githubusercontent.com/61201874/232917070-f5aa20be-9470-4072-9eb0-39f408a614af.png)
```
# prikažemo porazdelitev vzrokov smrti za vsak spol
X = moski_po_vzrokih
df_moski = pd.DataFrame(moski_po_vzrokih)
df_zenske = pd.DataFrame(zenske_po_vzrokih)
x_axis = np.arange(len(X))

plt.bar(x_axis - 0.2, df_moski.values[0], 0.4, label = 'Moški')
plt.bar(x_axis + 0.2, df_zenske.values[0], 0.4, label = 'Ženske')

plt.xticks(x_axis, X)
plt.xlabel("Vzroki smrti")
plt.ylabel("Število smrti")
plt.title("Primerjava vzrokov smrti za vsak spol")
plt.legend()
plt.xticks(rotation=90)
plt.show()
```
<br>


**3.	Kako je naraščalo število smrti po Sloveniji?**<br>
**4.	Kakšen je vpliv korone na število smrti med leti 2020 in 2022?**<br>
* Razlika med številoma smrti dveh določenih let v posameznih regijah <br>
![animated_map](https://github.com/smoki599/PR22JKEVBMKLGSHJ/assets/79158550/5eddfa7a-1bfc-47a1-b255-a2305c4808c1)
* Po letu 2009 število smrti narašča.
* Leta 2020 je število smrti zelo hitro začelo naraščati, lahko sklepamo da zaradi korone.
* Pred letom 2008 je umrlo več moških kot žensk, po letu 2008 pa več žensk kot moških.

<img width="743" alt="graf1" src="https://github.com/smoki599/PR22JKEVBMKLGSHJ/assets/79158550/068b4d32-4678-4b26-8f57-8845f8dcfb2a">

```
# prikažemo porazdelitev števila smrti za vsak spol
X = list(moski_po_letih.keys())
Y1 = list(moski_po_letih.values())
Y2 = list(zenske_po_letih.values())
Y1_prebivalci = list(m_prebivalstvo_po_letih.values())
Y2_prebivalci = list(z_prebivalstvo_po_letih.values())

fig, ax1 = plt.subplots(figsize=(10, 5))

ax1.set_xlabel('Leto')
ax1.set_ylabel('Število smrti')
ax1.set_title('Naraščanje števila smrti po letih')
ax1.plot(X, Y1, label='Moški - Smrti')
ax1.plot(X, Y2, label='Ženske - Smrti')
ax1.tick_params(axis='y')
ax1.legend(loc='upper left')

ax2 = ax1.twinx()
ax2.set_ylabel('Število smrti na 1000 prebivalcev')
ax2.plot(X, Y1_prebivalci, '--', label='Moški - smrti na 1000')
ax2.plot(X, Y2_prebivalci, '--', label='Ženske - smrti na 1000')
ax2.tick_params(axis='y')

fig.tight_layout()
plt.xticks(rotation=90)
plt.legend(loc='upper right')
plt.show()
```
<br>

<br>

**5. Primerjava števila smrti z drugimi EU državami** <br>
* Iz grafa lahko vidimo, da največ ljudi umre v Bulgariji.
* Najmanj ljudi umre na Islandiji in v Azerbaijanu.
* V Sloveniji je približno 10 smrti na 1000 prebivalcev na leto.
![graf6](https://github.com/smoki599/PR22JKEVBMKLGSHJ/assets/79158550/33901c6a-31c1-4173-87ec-3b878583dab6)
