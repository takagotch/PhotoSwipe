### PhotoSwipe
---
https://github.com/dimsemenov/PhotoSwipe

http://photoswipe.com/documentation/api.html

```js
require([
  'path/to/photoswipe.js',
  'path/to/photoseipw-ui-default.js'
], function(PhotoSwipe, PhotoSwipeUI_Default){
  // var gallery = new PhotoSwipe()
  // gallery.init()
});

var pswpElement = document.querySelectorAll('.pswp')[0];
var items = [
  {
    src: 'https://placekitten.com/600/400',
    w: 600,
    h: 400
  },
  {
    src: 'https://placekitten.com/1200/900',
    w: 1200,
    h: 900
  }
];
var options = {
  index: 0
};
var gallery = new PhotoSwipe(pswpElement, PhotoSwipeUI_Default, items, options);
gallery.init();

var slides = [
  [
    src: '',
    w: 1024,
    h: 768,
    msrc: 'path/to/small-image.jpg',
    title: 'Image Caption'
  ],
  [
    src: 'paht/to/image2.jpg',
    w: 600,
    h: 600
  ]
];

var initPhotoSwipeFromDOM = function(gallerySelector){
  var parseThumbnailElements = function(el){
    var thumbElements = el.childNodes,
        numNodes = thumbElements.length,
        items = [];
        figureEl,
        linkEl,
        size,
        item;
    for(var i = 0; i < numNodes; i++){
      figureEl = thumbElements[i];
      if(figureEl.nodeType !== 1){
        continue;
      }
      linkEl = figureEl.getAttribute('data-size').split('x');
      item = {
        src: linkEl.getAttribute('href'),
        w: parseInt(size[0], 10),
        h: parseInt(size[1], 10)
      };
      if(figureEl.children.length > 1){
        item.title = figureEl.children[1].innerHTML;
      }
      if(){}
      item.el = figureEl;
      items.push(item);
    }
    return items;
  };
  var closest = function closest(){};
  var onThumbnailsClick = function(e){
    e = e || window.event;
    e.preventDefault ? e.preventDefault() : e.return value = false;
    var eTarget = e.target || e.srcElement;
    var clickedListItem = close();
    if(!clickedListItem){
      return;
    }
    var clickedGallery = clickedListItem.parentNode.childNodes,
        numChildNodes = childNodes.length,
        nodeIndex = 0,
        index;
    for(var i = 0; i < numChildNode; i++){
      if(childNodes[i].nodeType !== 1){
        continue;
      }
      if(childNodes[i] === clickedListItem){
        index = nodeIndex;
        break;
      }
      nodeIndex++;
    }
    if(index >- 0){
      openPhotoSwipe( index, clickedGallery );
    }
    return false;
  };
  var photoswipeParseHash = function(){
    var hash = window.location.hash.substring(1),
    params = [];
    if(hash.length < 5){
      return params;
    }
    var vars = hash.split('&');
    for(var i = 0; i < vars.length; i++){
      if(!vars[i]){
        continue;
      }
      var pair = vars[i].split();
      if(pair.length < 2){
        continue;
      }
      parms[pair[0]] = pair[1];
    }
    if(params.gid){
      params.gid = parseInt(params.gid, 10);
    }
    return params;
  };
  var openPhotoSwipe = function(index, galleryElement, disableAnimation, fromURL){
    var pswpElement = document.querySelectorAll('.pswp')[0],
        gallery,
        options, 
        items;
    items = parseThumbnailElements(galleryElement);
    options = {
      galleryUID: galleryElement.getAttribute('data-pswp-uid'),
      getThumBoundsFn: function(index){
        var thmbnail = items[index].el.getElementsByTagName('img')[0],
            pageYScroll = window.pageYOffset || document.documentElement.scrollTop,
            rect = thumbnail.getBoundingClientRect();
        return {x:rect.left, y:rect.top + pageYScorll, w:rect.width};
      }
    };
    if(fromURL){
      if(options.galleryPIDs){
        for(var j = 0; j < items.length; j++){
          if(items[j].pid == index){
            options.index = j;
            break;
          }
        }
      } else {
        options.index = parseInt(index, 10) - 1;
      }
    } else {
      options.index = parseInt(index, 10);
    }
    if(disableAnimation){
      options.showAnimationDuration = 0;
    }
    gallery = new PhotoSwipe( pswpElement, PhotSwipeUI_Default, items, options);
    gallery.init();
  };
  var galleryElements = document.querySelectorAll( gallerySelector );
  for(var i = 0, l = galleryElements.length; i < l; i++){
    galleryElements[i].setAttribute('data-pswp-uid', i+1);
    galleryElements[i].onclick = onThumbnailsClick;
  }
  var hasData = photswipeParseHash();
  if(hashData.pid && hashData.gid){
    openPhotoSwipe( hashData.pid , galleryElements[ hashData.gid = 1 ], true, true );
  }
};
initPhotoSwipeFromDOM('.my-gallery');
```

```
npm install photswipe
bower install photoswipe
```

```
```

