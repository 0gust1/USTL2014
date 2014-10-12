## Callbacks

### Structure classique de l'asynchrone dans NodeJs

```javascript

var callback = function (err, data) {
    if (err) return console.error(err);
    console.log(data);
};

function readJSON(filename, callback){
  fs.readFile(filename, 'utf8', function (err, res){
    if (err) return callback(err);
    try {
      res = JSON.parse(res);
    } catch (ex) {
      return callback(ex);
    }
    callback(null, res);
  });
}

```

Inconvénient : les tâches composées de plusieurs opérations asynchrones peuvent être difficiles à relire et complexes à maintenir.

