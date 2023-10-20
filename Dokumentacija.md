---


---

<h1 id="zadaca-2---er-model---video-klub">Zadaca 2 - ER MODEL - Video Klub</h1>
<p>Ovaj dokument opisuje proces kreiranja ER dijagrama i primjenu DML upita za upravljanje podacima u bazi podataka “VIDEO KLUB”.</p>
<h2 id="er-dijagram">ER Dijagram</h2>
<p>U skladu sa specifikacijama, kreiran je ER dijagram za bazu podataka “VIDEO KLUB”. Dijagram prikazuje entitete i njihove veze. Evo dijagrama:</p>
<p><img src="https://i.imgur.com/jh8D9wA.png" alt="er dijagram"></p>
<p>Dijagram obuhvata sljedeće entitete:</p>
<ul>
<li>Film</li>
<li>Reziser</li>
<li>Glumac</li>
<li>FilmGlumci (relaciona tabela za veze između filmova i glumaca)</li>
<li>ReziserFilm (relaciona tabela za veze između rezisera i filmova)</li>
</ul>
<h2 id="relacioni-model">Relacioni model</h2>
<p>Tabele su kreirane koristeći sljedeće upite:</p>
<pre><code>CREATE TABLE z2_film (
    id INT PRIMARY KEY AUTO_INCREMENT,
    naslov VARCHAR(255) NOT NULL,
    reziser VARCHAR(255) NOT NULL,
    rejting INT NOT NULL,
    godina INT NOT NULL,
    nominacije INT,
    dobijeneNagrade INT
)

CREATE TABLE z2_glumci (
	id INT PRIMARY KEY AUTO_INCREMENT,
	imePrezime VARCHAR(255) NOT NULL,
	datumRodjenja DATE NOT NULL,
	datumSmrti DATE
)

CREATE TABLE z2_reziseri (
	id INT PRIMARY KEY AUTO_INCREMENT,
	imePrezime VARCHAR(255) NOT NULL,
	datumRodjenja DATE NOT NULL,
	datumSmrti DATE
)

CREATE TABLE z2_filmGlumac (
	filmId INT,
	glumacId INT,
	tipUloge VARCHAR(255),
	PRIMARY KEY (filmId, glumacId),
	FOREIGN KEY (filmId) REFERENCES z2_film(id),
	FOREIGN KEY (glumacId) REFERENCES z2_glumci(id)
)

CREATE TABLE z2_reziseriFilm (
	reziserId INT,
	filmId INT,
	PRIMARY KEY (reziserId, filmId),
	FOREIGN KEY (reziserId) REFERENCES z2_reziseri(id),
	FOREIGN KEY (filmId) REFERENCES z2_film(id)
)
</code></pre>
<h2 id="dml-komande">DML komande</h2>
<p>DML - Data Manipulation Language - SELECT, INSERT, DELETE, UPDATE<br>
U screenshot-u ispod sam koristio INSERT komande da unesem ove podatke u odgovarajuće tabele. Sve sto nije bilo označeno kao <code>NOT NULL</code> sam izostavio iz unosa, kao i ID koji se ima <code>AUTO_INCREMENT</code> podešen.</p>
<p><img src="https://i.imgur.com/QzNzf43.png" alt="DML"></p>

