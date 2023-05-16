Song Tracker, Uta George Adrian, grupa 1121

MODIFICARILE SUNT IN BRANCH-UL: "BRANCH_NOU".
Documentația proiectului – Song Tracker:

Proiectul Song Tracker este o aplicație creată pentru a vă ajuta să urmăriți și să organizați muzica preferată. Scopul său principal este să ofere utilizatorilor o modalitate convenabilă de a descoperi, sterge și gestiona melodiile preferate.

Descriere problema:
Aplicatia are rolul de a pune la dispozitie niste melodii, care pot fi sortate, cautate si sterse din playlist.


Descriere API:

API-ul utilizat pentru partea de backend este un API simplu, care permite funcționalități de get/post/delete într-o bază de date NOSQL.

Flux de date:

Utilizatorul intră în pagina de insert unde adaugă datele necesare despre film (numele, genul, director, actori, rating și dacă a fost vizionat sau nu) și salvează în baza de date. În urma salvării, datele sunt afișate în pagina principală. În această pagină datele pot sa fie vizualizate sau șterse. De asemenea, componenta de chat oferă posibilitatea de a discuta cu un ChatBot ce este antrenat să ofere recomandări despre filme.

Exemple de Request/Response, metode HTTP și autorizare servicii:

În cadrul componentei de Chat se folosește un API Call către OpenAI, unde este specificat ce fel de răspunsuri dorim să primim. Configurarea este următoarea:

MESSAGE: {
		'role': 'system',
		'content': 'You are a movie critic. You respond with recommendations and other details about movies',
	},
	TEMPERATURE: 1,
	MAX_TOKENS: 100,
Pentru utilizarea acestui serviciu am folosit Secret KEY-ul oferit de OpenAI pe care l-am stocat in fișierul .env din proiect.

const configuration = new Configuration({ apiKey: process.env.OPENAI_API_KEY, });

Răspunsul primit de la API-ul OpenAI este mai apoi afișat utilizatorului în componenta chat.

Exemplu de request POST către backend (Metoda HTTP de tipul POST):

Modul de trimitere date către backend-ul nostru: fetch("/api/records", { method: "POST", headers: { "Content-Type": "application/json", }, body: JSON.stringify(data), })

Iar funcția de POST din cadrul serverului arată astfel:

else if(req.method === 'POST') {
	const record = req.body;
	const result = await postRecord(record);
	return sendOk(res, result);
}
Descriere tehnologii cloud folosite:

Pentru dezvoltarea proiectului, s-au utilizat următoarele tehnologii cloud:

Next.js: un framework React pentru crearea de aplicații web și mobile.

MongoDB: o bază de date NoSQL cu scalabilitate orizontală și verticală.

OpenAI API: un API care furnizează instrumente de inteligență artificială pentru dezvoltatori.

Detalii despre aplicatie:

Aceasta este o aplciatie de tip Saas. O aplicație de tip Software-as-a-Service (SaaS) este o platformă software care este furnizată sub formă de serviciu prin intermediul internetului. Utilizatorii pot accesa și utiliza aplicația prin intermediul unui browser web, fără a fi nevoie să instaleze sau să gestioneze software-ul pe propriul lor sistem.
