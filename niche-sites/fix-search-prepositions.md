# Fix Pagefind Search: Stop Word Filtering

Check if this project uses Pagefind for search. If it does, check whether the `PagefindUI` initialization already filters out stop words (prepositions, articles) via a `processTerm` callback. If it does NOT filter stop words, add a `processTerm` option to strip them before searching.

Find where `new PagefindUI(...)` is called and update it to:

```js
var stopWords = ['de','del','el','la','los','las','un','una','unos','unas','en','con','por','para','al','a','y','o','e','que','se','su','es','lo','le','les','nos','me','te','mi','tu','si','no','ni','the','a','an','in','on','of','for','to','and','or','is','it','at','by','as','be','do','if','so','up','my','we','he','us'];
new PagefindUI({ element: container, showImages: false, processTerm: function(term) {
  return term.split(/\s+/).filter(function(w) { return stopWords.indexOf(w.toLowerCase()) === -1; }).join(' ');
} });
```

Keep any existing options (like `element`, `showImages`, `showSubResults`, etc.) — just add `processTerm` alongside them. Do not remove or change anything else.

This prevents searches like "Seguro de Auto" from matching every page containing "de".
