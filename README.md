# FINDWORK - Lavoro Javascript, America, Role  
<h4>Repository creata per l'appello di dicembre 2021.</h4>

# Applicazione

<p>
Lo scopo dell'applicazione permette all'utente di trovare offerte di lavori riguardanti il linguaggio Javascript.              
Inoltre, il sistema dovrà generare delle statistiche dai risultati ottenuti.                     
I risultati delle ricerche e le statistiche potranno essere filtrati tramite filtri opportuni.              
Per facilitare l'utente, l'applicazione suggerisce il nome di 5 città americane su cui fare le ricerche.  

</p>

# Rotte Applicazione

<p>
Per le chiamate di tipo <b>Post</b> i parametri vengono passati attraverso un <b></b>.                       
I parametri che dovranno essere passati sono:
<ul>
  <li>"luogo": (rappresenta il nome della città dove viene offerto il lavoro)</li>

 <li>"remoto": (indica se il lavoro è da remoto o no, quindi assume due valori -> true o false)</li>

 <li>"orario": (rappresenta il tipo di contratto: part-time o full-time o a contratto)</li>

 <li>"ruolo": (indica la mansione del lavoro  es. Software Engineers)</li>
  
 <li>"data": (indica la data di pubblicazione dell'annuncio)</li>
</ul>
<h3> Regole scrittura <b>Body</b>: </h3>

<h2>1.</h2>
<table>
  <tr><td>Tipo</td><td>Path</td></tr>
  <tr><td>GET</td><td>localhost:8080/annunci</td></tr>
</table>

Fornisce all'utente tutti gli annunci di lavoro riguardanti il linguaggio Javascript.

<br><b>Esempio: </b> di seguito vengono riportati alcuni di tutti gli annunci generati</br>


<h3>Chiamata : localhost:8080/annunci </h3>                   

![getAnnunci](https://user-images.githubusercontent.com/67264863/144684584-120734f6-8c60-4798-a9a6-a7b30f4a2366.png)

<h3>Risposta :</h3>

![a4](https://user-images.githubusercontent.com/67264863/144684596-746a003e-99e8-4f43-8caf-c9bec6571192.png)
![a1](https://user-images.githubusercontent.com/67264863/144684597-ad22b6f2-6512-4e15-b148-99894a199f43.png)
![a3](https://user-images.githubusercontent.com/67264863/144684600-156cbca0-a4f0-4a10-8606-0a149b49c80e.png)

<h2>2.</h2>
<table>
  <tr><td>Tipo</td><td>Path</td></tr>
  <tr><td>GET</td><td>localhost:8080/tips</td></tr>
</table>

Fornisce all'utente ii nome di cinque città americane su cui poter fare successivamente filtri o statistiche.

<br><b>Esempio: </b></br>


<h3>Chiamata : localhost:8080/tips </h3>    

![getTips](https://user-images.githubusercontent.com/67264863/144685218-82205472-8130-4134-b53b-db166d3dbc31.png)

<h3>Risposta :</h3>

![t1](https://user-images.githubusercontent.com/67264863/144685206-e7b5a841-18cd-4c72-bfaa-1956392f8f35.png)

<h2>3.</h2>
<table>
  <tr><td>Tipo</td><td>Path</td></tr>
  <tr><td>POST</td><td>localhost:8080/filters</td></tr>
</table>

Fornisce all'utente gli annunci di lavoro filtrati per i vari parametri forniti dall'utente.
<br>I parametri da inserire nel <b>Body</b> sono: "luogo", "remoto", "orario", "ruolo" e "data".
<br>E' possibile inserire più filtri contemporaneamente.
<br>Inoltre è possibile inserire più città per richiesta nel parametro luogo.
<br>Se non viene fornito nessun parametro dall'utente si otterà la lista completa degli annunci.

<br><b>Esempio: </b></br>

<h3>Chiamata : localhost:8080/filters </h3>

![getFilt](https://user-images.githubusercontent.com/67264863/144686568-00985ea3-bd53-4dd2-be9c-75ef45eefc29.png)

<h3>Body : </h3>
{ </br>
 "luogo" : "Plano", </br>
 "remoto" : false, </br>
 "orario" : "full time" </br>
} </br>
<br></br>

![2bodyFilter](https://user-images.githubusercontent.com/67264863/144915557-4c626288-7c5f-450c-9f32-04218308b82d.png)


<h3>Risposta :</h3>

![f2](https://user-images.githubusercontent.com/67264863/144686065-be956894-0647-4ee4-85f7-c0f79b751cc3.png)
![f3](https://user-images.githubusercontent.com/67264863/144686067-b9c5c992-b66b-4671-84b6-164dbb420111.png)

In questo caso vengono restituiti all'utente solamente gli annunci in cui :
<br>
- il luogo è Plano; 
- remoto = false;
- orario è full time;
- mentre per quanto riguarda il ruolo e la data, non essendo stati specificati, gli annunci vengono filtrati indipendemente da essi. </br>


<h2>4.</h2>
<table>
  <tr><td>Tipo</td><td>Path</td></tr>
  <tr><td>POST</td><td>localhost:8080/stats</td></tr>
</table>

<br>Questa rotta fornisce le statistiche sugli annunci.</br>
Gli annunci vengono prima filtrati in base ai parametri inseriti nel body dall'utente e poi ne vengono effettuate le statistiche.<br>
Per effettuare statistiche su tutti gli annunci basta non inserire nulla nel <b> Body</b> : { }.<br>
E' possibile effettuare statistiche su più città e su più parametri contemporaneamente. 

<br><b>Esempio: </b></br>

<h3>Chiamata : localhost:8080/stats</h3> 

![4getStat](https://user-images.githubusercontent.com/67264863/145389065-21ed7482-bb8f-47df-b95e-bd1316c0d93f.png)

<h3>Body :</h3>

{ </br>
 "luogo" : "Plano" </br>
} </br>



![3bodyStat](https://user-images.githubusercontent.com/67264863/145388393-9ee0a0d0-1ff5-4d65-b056-616adb459bf7.png)

<ul>
  <li>il luogo è Plano; </li>
  <li> essendo specificato solo il luogo verranno filtrati gli annunci per quel luogo e effettuate le statistiche indipendemente da ruolo, data, orario e remoto. </li>
</ul>

<h3>Risposta :</h3>

![3esempioStat](https://user-images.githubusercontent.com/67264863/145389025-51f46b12-dd8a-49c0-9b6d-a68d44538268.png)

Nella risposta saranno indicati : </br>
il numero totale degli annunci su cui sono state effettuate le statistiche ; </br>
il numero di lavori full time, part time e a contratto e le relative percentuali ; </br>
il numero di lavori da remoto con relativa percentuale ; </br>
il numero massimo e minimo di Keyword trovate negli annunci ; </br>
la Top 5 dei ruoli più richiesti ; </br>
i linguaggi richiesti insieme al JAVASCRIPT.


</p>

# UML

<ul><li>CASO D'USO</li></ul>

![3casoduso](https://user-images.githubusercontent.com/67264863/145387670-5b4ab41c-5229-4352-a86f-65950f3f5aed.png)

<ul><li>CLASSI</li></ul>

![main](https://user-images.githubusercontent.com/67264863/144682982-731ac431-a9be-4a72-a16d-db4be3a65c5c.png)
![3classeJsonParser](https://user-images.githubusercontent.com/67264863/145410846-033bcc64-44d3-42d4-9282-1d3cfe40d54b.png)
![3classeModel](https://user-images.githubusercontent.com/67264863/145410905-a9e0774d-2522-4bfd-998d-daecfdf8e119.png)
![2classeFindWorkApi](https://user-images.githubusercontent.com/67264863/145054347-050acfa7-b9e7-4960-92db-e611aae7eb32.png)
![3classeController](https://user-images.githubusercontent.com/67264863/145410914-b724236a-a09c-4155-89f2-efcfce9f9c9b.png)
![3classeFilter](https://user-images.githubusercontent.com/67264863/145410810-25283768-56ee-467f-8929-49c330eb6a00.png)
![3classeStat](https://user-images.githubusercontent.com/67264863/145410867-e49caa04-beb0-44e3-a8a2-ee963188dfcf.png)
![3classeException](https://user-images.githubusercontent.com/67264863/145411524-5ff1047a-406e-4cf2-9d5c-35852aa12412.png)

<ul><li>SEQUENZE</li></ul>

![2sequenzaJob](https://user-images.githubusercontent.com/67264863/145053850-d60f51a1-f227-49c7-82cf-e2368bf4cfdc.png)
![2sequenzaFiltri](https://user-images.githubusercontent.com/67264863/145053878-0b59f4c0-361d-4ed6-b709-edc379c1dcd1.png)
![3sequenzaStat](https://user-images.githubusercontent.com/67264863/145414438-fd558c1b-0888-463b-a49e-d47fdeb7acd9.png)
![sequenzaCitta2](https://user-images.githubusercontent.com/67264863/144910113-61fcc309-e700-427b-a0a8-815d9426ba37.png)

# Autori

<table>
<tr><td>Nome e Cognome</td><td>Contributo</td><td>Email</td></tr>
<tr><td>Fiore Garzarella</td><td>50%</td><td><a href="S1089186@studenti.univpm.it">S1089186@studenti.univpm.it</a></td></tr>
<tr><td>Christian Parente</td><td>50%</td><td><a href="S1089031@studenti.univpm.it">S1089031@studenti.univpm.it</a></td></tr>
</table>

