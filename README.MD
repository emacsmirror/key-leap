# Key-leap-mode
## A superb way of leaping between lines

Key-leap-mode is a minor mode for Emacs that allows you to quickly jump to any visible line in the current window. When the mode is active, it will populate the margin of the buffer's window with a set of unique three-letter keywords. 
By calling the interactive function `key-leap-start-matching`, you can jump to any visible line by typing the keyword of that line.

![demo](demo.gif)

It can be enabled in a buffer by calling `M-x key-leap-mode`.

## Customization

The function `key-leap-set-key-chars` allows you to specify which characters to use in each of the three positions of the keywords. For instance, adding the following to your config
```elisp
(key-leap-set-key-chars '(?h ?t ?n ?s)
                        '(?a ?o ?e ?u)
                        '(?h ?t ?n ?s))
```
will make key-leap-mode generate 64 keys that are easy to type on a dvorak layout.
By default, it will generate 125 keys from the letters of the home-row of a qwerty layout.
It is recommended to use a suitably large number of different characters for key-leap to use. The number of combinations of characters should be bigger than the number of possible visible lines for your setup, but not too much bigger than that. 

After leaping to a new line, it will run the hook `key-leap-after-leap-hook`. To make it move the point to the first non-whitespace character of the line after leaping, add the following to your config:
```elisp
(add-hook 'key-leap-after-leap-hook 'back-to-indentation)
```

For more info on customization, please see the commentary in the file `key-leap-mode.el`.

## Motivation

This mode was inspired by the `avy-goto-line` command of [avy-mode](https://github.com/abo-abo/avy). I wanted that kind of functionality but with the following differences:
* The keys should be always visible, no overlays appearing in the buffer's contents.
* There should be more control over in what sequence the characters of the keys appear.

Key-leap-mode was the result.

## Contributing

This is still in the early stages of development, and it has a lot of issues to iron out. Bug reports, suggestions and pull requests are welcome!

## Contact

Visit [@rykarn](https://twitter.com/rykarn) if you want to say hi.

## License

GPL v3