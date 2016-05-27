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
    
