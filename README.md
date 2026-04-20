# Nuxt Nieuws Project

Dit project is gebouwd met **Nuxt** en gebruikt een **mock API** met `json-server`.

## Vereisten

Voordat je het project kunt draaien moet je het volgende geïnstalleerd hebben:

* **Node.js** (https://nodejs.org/)
* **npm** (wordt automatisch geïnstalleerd met Node.js)

Je kunt controleren of ze geïnstalleerd zijn met:

```bash
node -v
npm -v
```

---

# Installatie

## 1. Clone de repository

Clone de repository naar je computer:

```bash
git clone <your-repository-url>
```

## 2. Ga naar de projectmap

Navigeer naar de projectmap:

```bash
cd <your-project-folder>
```

## 3. Installeer dependencies

Dit project gebruikt **node modules**, deze staan niet in de repository.
Installeer ze daarom eerst met:

```bash
npm install
```

Dit installeert alle benodigde dependencies voor het Nuxt project.

---

# De Nuxt Applicatie Starten

Start de Nuxt development server met:

```bash
npm run dev
```

Na het uitvoeren van dit commando zal er een link in de terminal verschijnen zoals:

```
http://localhost:3000
```

Als je op deze link klikt in de terminal zal de website openen in je browser.

---

# De Mock API Starten

Dit project gebruikt **json-server** als mock backend.

Terwijl de Nuxt server draait, open je **een tweede terminal**.

## 1. Ga naar de mock map

```bash
cd mock
```

## 2. Start de mock server

Voer het volgende commando uit:

```bash
npx json-server db.json --port 3001
```

De mock API zal nu draaien op:

```
http://localhost:3001
```

---

# Het Hele Project Draaien

Zowel de **Nuxt applicatie** als de **mock API** moeten tegelijkertijd draaien.

### Terminal 1 (Nuxt App)

```bash
npm install
npm run dev
```

### Terminal 2 (Mock API)

```bash
cd mock
npx json-server db.json --port 3001
```

---

# Technologieën Gebruikt

* **Nuxt**
* **Vue**
* **Tailwind CSS**
* **json-server**

---

# Opmerkingen

* Zorg ervoor dat je eerst **npm install** uitvoert voordat je het project start.
* Laat **beide terminals open** terwijl je aan de applicatie werkt.
* Sommige functies werken alleen als de **mock API** draait.
