# Romanization

Give me any Unicode string, and I'll give you its romanization (in pure ASCII).

## Why it?

I had that idea when I was developing an app to manage contacts, when the contacts had to be sorted by their names. As there are countless characters in Chinese, it's impossible to sort by a "Chinese alphabet", and the names of contacts, cities or other things are usually sorted by their *Pinyins* (a kind of romanization of Chinese) in the order of A-Z, and that's why we need the romanization of Chinese characters.

We do have libraries of getting the Pinyin of Chinese sentences, Romaji of Japanese sentences, and also romanizations of Russian and similar languages. But there is no availible library to get the romanization of ANY scripts--in any programming languages. This project aims to provide a way to generate the romanization of different scripts, and it should suits our multiple needs.

### Pure ASCII

You may think it's okay to leave all Latin characters as they are. Unfortunately the diacritics of Latin characters disturbs the needs like sorting. There should not be no non-ASCII Latin character on the result of the convertion, some of which can be simply removed and some can be converted into equal letter combinations (like `ae` for `æ`).

Also there are some non-ASCII punctuations like `（`. It will be okay just to convert them into their ASCII forms (like `(`).

### Suitable for different languages using the same script

Some existing awesome libraries like [Unidecode](https://github.com/avian2/unidecode) aim to generate ASCII transliterations of Unicode texts, and it mentions:

> With Japanese and Chinese this is even more evident because the same letter can have very different transliterations depending on the language it is used in. Since Unidecode does not do language-specific transliteration (see next question), it must decide on one. For certain characters that are used in both Japanese and Chinese the decision was to use Chinese transliterations.

Different languages using the same script may have different pronunciations on the same character. For example, “正”(U+6B63) reads `zheng` on Chinese but `sei` on Japanese. To solve that problem we have to specify the language used during the convention.

## How to do?

As there is no library to do universal romanizationizing works, we have to provide libraries in different programming languages. The most important ones are:

+ ANSI C, for projects using C/C++/Rust/Go/Zig/V or other languages that can call C functions easily.
+ JavaScript (not TS), which is used widely for frontend projects.

And other popular languages:

+ Pure Python: Although C libraries can be packed as Python packages and be easily imported via `pip`, it's more useful to write it in pure Python to ensure the maximum compatibility.
+ Java and C# for related runtimes.
+ Dart for Flutter projects.

They are the Tier 1 and Tier 2 programming languages of this project, so we will have libraries like `cromanization` and `jsromanization` in the future. Contributions to other languages are also welcomed.