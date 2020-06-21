
İlk olarak, onun nasıl *yapılmadığını* görelim:

```js
function clear(elem) {
  for (let i=0; i < elem.childNodes.length; i++) {
      elem.childNodes[i].remove();
  }
}
```

O calışmayacak, çünkü `remove()` çağrısı `elem.childNodes` koleksiyonunu kaydırır, bu yüzden elementler her zaman "0"(sıfır) dizininden başlar. Ama `i` artar, ve bazi elemetler atlanmis olur. 

`for..of` ilmegi(loop) de aynısını yapar.
Doğru degişken(variant) şöyle olabilir :

```js
function clear(elem) {
  while (elem.firstChild) {
    elem.firstChild.remove();
  }
}
```

Ve aynısını yapmanın daha basit bir yolu da var:

```js
function clear(elem) {
  elem.innerHTML = '';
}
```
