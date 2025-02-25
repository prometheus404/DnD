Il testo cifrato viene presentato in una tabella con 4 righe e un numero di colonne 4 volte il numero di lettere della parola più lunga presente nella frase.

un testo cifrato può essere per esempio:

| 210 | 105 | 210 | 1   | 210 | 42  | 210 | 1   | 210 | 210 | 210 | 1   | 21  | 21  | 21  | 1   | 3   | 3   | 3   | 1   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 42  | 10  | 6   | 1   | 210 | 15  | 70  | 1   | 105 | 210 | 21  | 1   | 21  | 7   | 1   | 1   | 3   | 1   | 3   | 1   |
| 42  | 15  | 42  | 1   | 210 | 14  | 70  | 1   | 105 | 6   | 7   | 1   | 7   | 3   | 3   | 1   | 3   | 1   | 3   | 1   |
| 42  | 35  | 14  | 1   | 210 | 3   | 210 | 1   | 210 | 10  | 210 | 1   | 21  | 21  | 21  | 1   | 3   | 3   | 3   | 1   |

La chiave è un numero primo per ogni parola.
per esempio: 2,3,5,7

Per decodificare il testo è sufficiente per ogni parola da trovare, cercare tutti i numeri nella tabella che sono multipli della chiave corrispondente
seguendo l'esempio precedente la prima parola, avente chiave 2, viene decodificata come:
```
* * *** ***
*** * *  *
* * ***  *
* * * * ***
```
dove per rendere evidente il pattern, gli elementi divisibili per 2 sono stati sostituiti con un `*` e gli altri con uno spazio vuoto.
Ciò che rimane è una scritta nel font 3x5 visibile nell'immagine seguente:
![[pixel_font.webp]]

Di seguito il codice python per generare e decodificare messaggi
```python
import functools


def encode(message, key, length, alphabet, gliph_size):
    g_x, g_y = gliph_size
    return [
        [
            (
                (
                    j // 4 < len(message)
                    and (j % 4 != 3)
                    and alphabet[message[j // 4]][i][j % 4] == 1
                    and key
                )
                or 1
            )
            for j in range((g_x + 1) * length)
        ]
        for i in range(g_y)
    ]


def merge(enc_txt1, enc_txt2):
    assert len(enc_txt1) == len(
        enc_txt2
    ), f"{len(enc_txt1)} is different from {len(enc_txt2)}"
    assert len(enc_txt1[0]) == len(enc_txt2[0])

    return [
        [enc_txt1[i][j] * enc_txt2[i][j] for j in range(len(enc_txt1[0]))]
        for i in range(len(enc_txt1))
    ]


def encode_multiple(messages, keys, alphabet, gliph_size):
    assert len(messages) == len(keys)
    max_len = max([len(m) for m in messages])
    return functools.reduce(
        merge,
        [
            encode(messages[i], keys[i], max_len, alphabet, gliph_size)
            for i in range(len(keys))
        ],
    )


def decode_graphical(encoded_message, keys):
    for k in keys:
        for msg in encoded_message:
            print(
                functools.reduce(
                    lambda a, b: a + b,
                    [(msg[i] % k == 0 and "*") or " " for i in range(len(msg))],
                )
            )
        print("-" * len(encoded_message[0]))


def to_table(msg):
    s = ""
    for m in msg:
        for pixel in m:
            s += f"{pixel:>6}"
        s += "\n"
    return s


alphabet = {
    "a": [[1, 1, 1], [1, 0, 1], [1, 1, 1], [1, 0, 1]],
    "b": [[1, 1, 0], [1, 1, 1], [1, 0, 1], [1, 1, 1]],
    "c": [[1, 1, 1], [1, 0, 0], [1, 0, 0], [1, 1, 1]],
    "d": [[1, 1, 0], [1, 0, 1], [1, 0, 1], [1, 1, 0]],
    "e": [[1, 1, 1], [1, 1, 0], [1, 0, 0], [1, 1, 1]],
    "f": [[1, 1, 1], [1, 0, 0], [1, 1, 0], [1, 0, 0]],
    "g": [[1, 1, 1], [1, 0, 0], [1, 0, 1], [1, 1, 1]],
    "h": [[1, 0, 1], [1, 1, 1], [1, 0, 1], [1, 0, 1]],
    "i": [[1, 1, 1], [0, 1, 0], [0, 1, 0], [1, 1, 1]],
    "j": [[1, 1, 1], [0, 1, 0], [0, 1, 0], [1, 1, 0]],
    "k": [[1, 0, 1], [1, 1, 0], [1, 1, 0], [1, 0, 1]],
    "l": [[1, 0, 0], [1, 0, 0], [1, 0, 0], [1, 1, 1]],
    "m": [[1, 1, 1], [1, 1, 1], [1, 0, 1], [1, 0, 1]],
    "n": [[1, 1, 1], [1, 0, 1], [1, 0, 1], [1, 0, 1]],
    "o": [[1, 1, 1], [1, 0, 1], [1, 0, 1], [1, 1, 1]],
    "p": [[1, 1, 1], [1, 0, 1], [1, 1, 1], [1, 0, 0]],
    "q": [[1, 1, 1], [1, 0, 1], [1, 1, 1], [0, 0, 1]],
    "r": [[1, 1, 1], [1, 1, 1], [1, 1, 0], [1, 0, 1]],
    "s": [[1, 1, 1], [1, 0, 0], [0, 1, 1], [1, 1, 1]],
    "t": [[1, 1, 1], [0, 1, 0], [0, 1, 0], [0, 1, 0]],
    "u": [[1, 0, 1], [1, 0, 1], [1, 0, 1], [1, 1, 1]],
    "v": [[1, 0, 1], [1, 0, 1], [1, 0, 1], [0, 1, 0]],
    "w": [[1, 0, 1], [1, 1, 1], [1, 1, 1], [1, 1, 1]],
    "x": [[1, 0, 1], [1, 1, 0], [0, 1, 1], [1, 0, 1]],
    "y": [[1, 0, 1], [1, 1, 1], [0, 1, 0], [0, 1, 0]],
    "z": [[1, 1, 1], [0, 1, 1], [1, 0, 0], [1, 1, 1]],
}

if __name__ == "__main__":
    gliph_size = (3, 4)  # gliphs are 3x4 pixels
    messages = ["hai", "perso", "the", "game"]  # ["lorem", "ipsum", "dolor", "sit"]
    keys = [2, 3, 5, 7]
    message_encoded = encode_multiple(messages, keys, alphabet, gliph_size)
    print(to_table(message_encoded))
    decode_graphical(message_encoded, keys)
```