# AryaAPI [![npm version](https://img.shields.io/npm/v/genius-lyrics-api.svg?style=flat)](https://www.npmjs.com/package/AryaAPI)

A JavaScript package that leverages [Genius API](https://genius.com/developers) to search and fetch song lyrics and album art.<br/>It doesn't use any native node dependencies and therefore, can be used on the client-side.

## Installation

Install with npm

```js
npm install --save AryaAPI
```

Or install with Yarn

```js
yarn add AryaAPI
```

## Usage

[Get the Genius Developer Access Token](https://genius.com/developers)
<br>

```js
import { GetLyrics, GetSong } from 'AryaAPI';
```

```js
const options = {
	apiKey: '7251827XXXXXX',
	title: 'Alone',
	artist: 'Alan Walker',
	optimizeQuery: true
};

getLyrics(options).then((lyrics) => console.log(lyrics));

getSong(options).then((song) =>
	console.log(`
	${song.id}
	${song.title}
	${song.url}
	${song.albumArt}
	${song.lyrics}`)
);
```

<br>

> :warning: You may get a CORS block error while testing on localhost. To bypass this, you need to disable Same-Origin Policy in your browser. You may follow the instructions [Here](https://stackoverflow.com/questions/3102819/disable-same-origin-policy-in-chrome).

<br>

## Types

```
type options {
	title: string;
	artist: string;
	apiKey: string;		// Genius developer access token
	optimizeQuery?: boolean; // Setting this to true will optimize the query for best results
	authHeader?: boolean; // Whether to include auth header in the search request. 'false' by default.
}

```

🚨 All properties in the options object are required except `optimizeQuery` and `authHeader`. If `title` or `artist` is unknown, pass an empty string.

```
type song {
	id: number;		// Genius song id
	title: string;          // Song title
	url: string;		// Genius webpage URL for the song
	lyrics: string;		// Song lyrics
	albumArt: string;	// URL of the album art image (jpg/png)
}

```

```
type SearchResult {
	id: number;		// Genius song id
	url: string;		// Genius webpage URL for the song
	title: string;		// Song title
	albumArt: string;	// URL of the album art image (jpg/png)
}
```

## Methods

AryaAPI exposes the following methods:

### `GetLyrics(options | url)`

Accepts [Options](#types) or the url to a Genius song. <br/>
Returns a promise that resolves to a string containing lyrics. Returns `null` if no lyrics are found.

### `GetAlbumArt(options)`

Accepts an [Options](#types) object. <br/>
Returns a promise that resolves to a url (string) to the song's album art. Returns `null` if no url is found.

### `GetSong(options)`

Accepts an [Options](#types) object. <br/>
Returns a promise that resolves to an object of type [song](#types). Returns `null` if song is not found.

### `SearchSong(options)`

Accepts an [Options](#types) object. <br/>
Returns a promise that resolves to an array of type [searchResult](#types). Returns `null` if no matches are found.

### `GetSongById(id: (number | string))`

Accepts a valid Genius song ID. IDs can be found using the `SearchSong` method. <br/>
Returns a promise that resolves to an object of type [song](#types).

## Support

If you this repo is make you happy then support me by joining @CyberSupportgROUP
