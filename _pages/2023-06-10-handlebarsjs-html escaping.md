## handlebarsjs Partials, html escaping

.hbs:
```
{{{content}}}
{{{address}}}
```

imgtxt.vash:
```
<div class="row imgtxt">
  <div class="col-6"><img id="myImg" src="{{image}}" width="1024" height="576"></div> <!--src-->
  <div class="col-6"><p>{{txt}}</p></div> <!--txt-->
</div>
```

.js
```
var Handlebars = require('handlebars');
if (json.data.template == 'imgtxt') {
	json.data.content = fs.readFileSync('src/template/imgtxt.vash', 'utf8').toString();
}

var tpl = Handlebars.compile(template);
var out = tpl(json.data);
// <p>I am a template!</p>
```

result:
html escaping {{{ }}} can insert html b, but b's {{ }} won't render.

imgtxt.vash part will show unrender {{txt}}.