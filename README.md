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

### Izvedene analize in glavne ugotovitve
Da bi odgovorili na vprašanja, ki smo si jih zadali, smo izdelali nekaj grafov:<br><br>
**1.	Kateri vzrok smrti je najpogostejši glede na statistično regijo?**<br>
* Največ ljudi (v vseh občinah) umre zaradi bolezni obtočil, drugi najpogostejši vzrok pa so infekcijske in parazitne bolezni.
* Najmanj ljudi (v vseh občinah) umre zaradi neoplazme.
* Pri skoraj vseh vzrokih je največ smrti v pomurski regiji.
* Najmanj smrti je v osrednjeslovenski regijii.

![Screenshot 2023-04-19 at 00 13 14](https://user-images.githubusercontent.com/61201874/232916631-56522e1c-0e37-442f-bc14-bde130b4d8b9.png)

Grafi vzrokov smrti po posameznih regijah:
![Screenshot 2023-04-18 at 22 09 43](https://user-images.githubusercontent.com/61201874/232918515-e4f38179-ef3b-4bbb-8686-f7c4ec9f8dbf.png)
![Screenshot 2023-04-18 at 22 09 57](https://user-images.githubusercontent.com/61201874/232918545-2138553c-d0a8-45d9-a61a-48b9cb4495aa.png)
![Screenshot 2023-04-18 at 22 10 09](https://user-images.githubusercontent.com/61201874/232918657-33d25a88-b576-4fe5-b329-96a4e2582151.png)
![Screenshot 2023-04-18 at 22 10 20](https://user-images.githubusercontent.com/61201874/232918674-6f948e93-6f5b-473b-bf23-861dfd547144.png)
![Screenshot 2023-04-18 at 22 10 34](https://user-images.githubusercontent.com/61201874/232918682-c07e4296-d1ef-42e3-a672-26f23171865d.png)
![Screenshot 2023-04-18 at 22 10 45](https://user-images.githubusercontent.com/61201874/232918713-b5fbcbb1-308c-41ae-8c46-a093833f5899.png)
```
#==============SEZNAM VZROKOV=============

Y = df['STATISTIÈNA REGIJA'][1:13]
frame = pd.DataFrame(data=smrti, index = vzroki)
frame.drop(vzroki[1:]).plot( y=Y, kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0)
plt.show()


frame = pd.DataFrame(data=smrti, index = vzroki)
frame.drop(returnAllBut(vzroki,1)[:]).plot( y=Y, kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0)
plt.show()

frame = pd.DataFrame(data=smrti, index = vzroki)
frame.drop(returnAllBut(vzroki,2)[:]).plot( y=Y, kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0)
plt.show()

frame = pd.DataFrame(data=smrti, index = vzroki)
frame.drop(returnAllBut(vzroki,3)[:]).plot( y=Y, kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0)
plt.show()

frame = pd.DataFrame(data=smrti, index = vzroki)
frame.drop(returnAllBut(vzroki,4)[:]).plot( y=Y, kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0)
plt.show()

frame = pd.DataFrame(data=smrti, index = vzroki)
frame.drop(returnAllBut(vzroki,5)[:]).plot( y=Y, kind='bar', title="Vzrok smrti v regijah na 1000 prebivalcev", figsize=(12,4), ylabel='Število smrti na 1000 prebivalcev"', rot=0)
plt.show()

frame = pd.DataFrame(data=smrti, index = vzroki)
frame.plot( y=Y, kind='bar', title="V comp", figsize=(12,8), ylabel='Število smrti na 1000 prebivalcev"', rot=0)
frame.plot

plt.xlabel("Vzrok smrti")
plt.ylabel("Število smrti na 1000 prebivalcev")
plt.title("Vzrok smrti v regijah na 1000 prebivalcev")
plt.legend()
plt.xticks(rotation=90)
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
* Po letu 2009 število smrti narašča.
* Leta 2020 je število smrti zelo hitro začelo naraščati, lahko sklepamo da zaradi korone.
* Pred letom 2008 je umrlo več moških kot žensk, po letu 2008 pa več žensk kot moških.

![Screenshot 2023-04-19 at 00 21 04](https://user-images.githubusercontent.com/61201874/232917806-3ae3c8b4-5340-4124-be59-4f18bb7ac9f2.png)
```
# prikažemo porazdelitev števila smrti za vsak spol
X = list(moski_po_letih.keys())
Y1 = list(moski_po_letih.values())
Y2 = list(zenske_po_letih.values())

plt.plot(X, Y1, label='Moški')
plt.plot(X, Y2, label='Ženske')

plt.xlabel('Leto')
plt.ylabel('Število smrti')
plt.title('Naraščanje vzrokov smrti po Sloveniji')
plt.xticks(rotation=90)
plt.legend()
plt.show()
```
