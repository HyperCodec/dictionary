# dictionary
This repository contains data scraped off of https://dictionaryapi.dev/ for use offline or to avoid ratelimit.
It has ~200k entries.

### File Structure
The model of the dictionary looks like this:
```ts
type WordData = {
    word: string,
    phonetic: string,
    phonetics: Array<Phonetic>,
    origin: string,
    meanings: Array<Meaning>,
    license: License,
    source_urls: Array<string>,
};

type Phonetic = {
    text: string,
    audio: string | null
};

type Meaning = {
    part_of_speech: string,
    definitions: Array<Definition>,
};

type Definition = {
    definition: string,
    example: string,
    synonyms: Array<string>,
    antonyms: Array<string>,
};

type License = {
    name: string,
    url: string,
};
```

In `dictionary.json`, there is an array of `WordData` objects sorted alphabetically by the `word` field. In `dictionary_multimap.json`,
the data is mapped in a way so that keys are words and values are `WordData` objects.

### License
In order to comply with the licenses of the scraped data (most of which is CC BY-SA 3.0), this repository has also been licensed under CC BY-SA 3.0.
For full details, visit: https://creativecommons.org/licenses/by-sa/3.0/
