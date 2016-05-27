# IntersectionObserver Examples

Mit IntersectionObservers ist es sehr einfach und vor allem ohne [Jank]() möglich, herauszufinden, ob ein Element gerade im Viewport sichtbar wird bzw. ihn verlässt. Das Besondere an IntersectionObservers (IO) ist, dass man dafür weder [getBoundingClientRect()](https://developer.mozilla.org/en-US/docs/Web/API/Element/getBoundingClientRect) abfragen, noch einen Scroll event handler anlegen muss.

IO sind gedacht und eignen sich für:

* Abfragen der Position von below the fold Inhalten und lazy loaden dieser
* Performante Infinite Scrolling Listen
* Sichtbarkeit von Elementen abfragen. Besonders interessant für Werbebanner.

Sie eignen sich nicht für Szenarien bei denen pixelgenaue Informationen, bspw. bei Animation, gefragt sind.

## IntersectionObserver erstellen

Man legt einen IntersectionObserver an und legt fest, welches Element *observed* werden soll.

	const io = new IntersectionObserver(entries => {
	
    	// Verfügbare Daten, wenn das Element den Viewport betritt oder verlässt
    	console.log(entries);
    });
    
    // Element, das observed werden soll
    const box = document.querySelector('.box');
    
    // .box observen
    io.observe(box);
    
Dieses Beispiel, erweitert durch eine Statusanzeige, kann man sich [hier](http://htmlpreview.github.io/?https://github.com/matuzo/IntersectionObserver-Examples/blob/master/simple.html) ansehen. Der Code ist auf [Github](https://github.com/matuzo/IntersectionObserver-Examples/blob/master/simple.html).

### Mehrere Elemente beobachten

Möchte man mehrere Elemente beobachten, empfiehlt es sich ein und den selben Observer dafür zu verwenden.

	const io = new IntersectionObserver(entries => {
    	console.log(entries);
    });
    
    // Elemente, die observed werden sollen
	const box1 = document.querySelector('.box');
    const box2 = document.querySelector('.box2');
        
    // .box1 und .box2 observen
    io.observe(box1);
    io.observe(box2);


Dieses Beispiel gibt es ebenfalls als [Demo] und auf [Github].

### Kindelemente innerhalb eines anderen Elements observen

Man kann dem Observer Optionen übergeben. Beispielsweise kann man festlegen, dass Elemente nicht innerhalb des Dokuments beoachtet werden sollen, sondern innerhalb eines anderen Elements.

	const io = new IntersectionObserver(entries => {
	
    	// Verfügbare Daten, wenn das Element den sichtbaren Bereich des 
    	// Elternelements betritt oder verlässt
    	console.log(entries);
    }, {

        // Festlegen welches Element das root-Element sein soll
        root: document.querySelector('.container')
    });
    
    // Element, das observed werden soll
    const box = document.querySelector('.box');
    
    // .box observen
    io.observe(box);
    
Dieses Beispiel gibt es natürlich auch als [Demo] und auf [Github].