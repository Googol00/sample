const express = require('express');
const mysql = require('mysql');

const app = express();

const connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: 'origin007',
  database: 'articles'
});

connection.connect((error) => {
  if(error) {
    console.log('error connecting: '+ error.stack);
    return;
  }
  console.log('success');
});

app.use(express.static('public'));

app.get('/', (req, res) => {
  res.render('top.ejs');
});

app.get('/info', (req, res) => {
  res.render('info.ejs');
});

app.get('/list', (req, res) => {
  connection.query(
    'SELECT * FROM article',
    (error, results) => {
      res.render('list.ejs', { article: results });
    }
  );
});

app.get('/emaxisneo', (req, res) => {
  res.render('emaxisneo.ejs');
});

app.get('/article/:id', (req, res) => {
  const id = req.params.id;
  connection.query(
    'SELECT * FROM article WHERE id = ?',
    [id],
    (error, results) => {
      res.render('article.ejs', { article: results[0] });
    }
  );
});

app.listen(3000);
