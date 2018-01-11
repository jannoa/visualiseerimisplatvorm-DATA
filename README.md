# visualiseerimisplatvorm-DATA

## Lahendus 1

Kasutan [test1_backup.csv](https://github.com/jannoa/visualiseerimisplatvorm-DATA/blob/master/test1_backup.csv) datat ja [logstashi](https://github.com/jannoa/visualiseerimisplatvorm-DATA/blob/master/test1.config) *kv* pluginat:

```
kv {
		source => "TAGS"
		field_split => ";"
		value_split => ":"
		target => "TAGS"
	}
```

Tulemus on:
![kv_plugin](https://user-images.githubusercontent.com/34548027/34842299-c4743bba-f713-11e7-9988-d6c0b6b95065.png)

Tekivad field-id aga puudulikud, nt
Isegi ku mul on CSV failis TAGS headi all olemas ka *cve:CVE-2018-0111;* väärtus siis loob ainult *cve:CVE-2014-0160;* põhjal field-i - miks just selle põhjal, ei tea ning miks teisest ei loo ka fieldi siis vist *kv* ei ole võimeline üksinda rohkemaks.

Lisaks ei loe CSV-st key välju nagu *contentms:...;* ja *contentms.ver:...*- miks? ei tea...


## Lahendus 2

Kasutan [test1.csv](https://github.com/jannoa/visualiseerimisplatvorm-DATA/blob/master/test1.csv) datat ja logstashi *json* pluginat:

```
json {
		source => "TAGS"
		target => "TAGS"
	}
```

Tulemus on:
![plugin_json](https://user-images.githubusercontent.com/34548027/34842016-e046c2fa-f712-11e7-919a-bcba1d645085.png)

Ei tekita eraldi field'i aga on otsitav ja saab luua pirukaid jne, nt:

![json_tulemus](https://user-images.githubusercontent.com/34548027/34842097-1ebe5bd8-f713-11e7-85ce-efb64796c348.png)

## Kokkuvõttes

Kui ei ole vaja, et tekiksid *field-id* siis võib vabalt kasutada *json* pluginat. 

