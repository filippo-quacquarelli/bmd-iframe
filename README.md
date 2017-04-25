# bmd-iframe
iFrame inside Bootstrap 3 modal

Questo plugin jQuery si occupa di "iniettare" un'iframe all'interno di una modale di Bootstrap 3, basta impostare un'attributo data col l'url dell'iframe, ad un bottone/link ed al click vedremo comparire la modale col nostro iframe.

Example: http://codepen.io/filippoq/pen/QwogWz

### Dipendenze
Questo plugin è studiato per le modali di Bootstrap 3, quindi richiede Bootstrap 3 e jQuery.

## Utilizzo

### html
Aggiungiamo il file bmd-iframe.js al nostro documento, fatto questo dobbiamo inserire la struttura html della modale di bootstrap nel footer (o dove preferite) e all'interno del modal-body, dobbiamo aggiungere un'iframe vuoto come nel seguente esempio:
```html
<div class="modal fade" id="myModal">
		<div class="modal-dialog">
			<div class="modal-content bmd-modalContent">

				<div class="modal-body">          
          <div class="close-button">
					<button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
         </div>
         <div class="embed-responsive embed-responsive-16by9">
				  <iframe class="embed-responsive-item" frameborder="0"></iframe>
         </div>
         
			</div>
		</div><!-- /.modal-content -->
	</div><!-- /.modal-dialog -->
</div><!-- /.modal -->
  ```
Nell'esempio illustrato oltre ad inserire l'iframe all'interno di modal-body l'ho già inserita anche all'interno del componente di bootstrap che rende gli iframe responsive (http://getbootstrap.com/components/#responsive-embed) per il resto è la struttura html di una classica modale.

Non ci resta che aggiungere un bottone coi nostri attributi personalizzati:
```html
<button type="button" class="bmd-modalButton" data-toggle="modal" data-target="#myModal" data-bmdSrc="https://www.youtube.com/embed/mWRsgZuwf_8" data-bmdWidth="640" data-bmdHeight="480" data-bmdVideoFullscreen="true">Youtube</button>
```
Vediamo come il bottone abbia i due classici attributi data (toggle, target) ed altri che andiamo ad illustrare, la classe bmd-modalButton è necessaria per abilitare la funzionalità:

data-bmdSrc deve contenere l'url che ogni iframe possiede (atributo src="") (required)

data-bmdWidth e data-bmdHeight imposta la larghezza ed altezza dell'iframe (attributi width ed height) sono facoltativi i valori di default sono 640x360px

data-bmdVideoFullscreen imposta l'attributo allowfullscreen solitamente utilizzato dai servizi come youtube o vimeo per abilitare il supporto a tutto schermo del video è facoltativo non inserirlo per non abilitarlo per esempio se usi l'iframe per una google maps.

### JavaScript
Non ci resta che abilitare il plugin:
```javascript
jQuery("#myModal").bmdIframe();
```
Agganciamo il plugin alla modale (#myModal) dovremmo farlo nel footer oppure abilitare la funzione al document.ready():
```javascript
jQuery(document).ready(function(){
  jQuery("#myModal").bmdIframe();
});
```
Abbiamo a disposizione anche una semplice api per cambiare alcuni valori di default, esempio:
```javascript
jQuery("#myModal").bmdIframe({
  classBtn: '.modalButton',
  defaultW: 1000,
  defaultH: 500
});
```
Nell'esempio abbiamo agganciato il plugin alla nostra modale come visto prima, in più abbiamo modificato 3 valori di default:

classBtn (string) serve a cambiare la classe di default da applicare al bottone, valore di default: '.bmd-modalButton'

defaultW (int) serve a cambiare la larghezza di default da applicare all'iframe, valore di default: 640

defaultH (int) serve a cambiare l'altezza di default da applicare all'iframe, valore di default: 360

Nell'esempio http://codepen.io/filippoq/pen/QwogWz sono incluse poche righe css che donano un aspetto più gradevole alla modale.

Caricare i contenuti esterni come video di youtube, vimeo, google maps ... all'interno di modali è un'ottimo modo per evitare di appesantire troppo la pagina, infatti nonostante i contenuti di questi widget vengono caricati in asincrono, all'ungano il tempo complessivo di caricamento pagina, rallentano la ui, aumentano il numero di richieste.

MIT LICENSE
