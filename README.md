# awaiterfall
async await simple waterfall.

###### install runkoa

npm install -g runkoa

```javascript
let Koa = require('koa'),
    app = new Koa(),
    awaiterfall = require('awaiterfall')

app.use(async function (ctx,next){
    const upper = _ => new Promise( res => res(_.toUpperCase()) )

    const reverse = _ => new Promise( res => res(_.split('').reverse().join('')) )

    const space = _  => new Promise( res => res(_.replace(/ {0,}/g,' ')) )

    ctx.body = await awaiterfall("tpircsavaj", upper, reverse, space)
})

app.listen(3000)
```