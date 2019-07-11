# crypt_io
crypto_io is a text interface showcasing the various cyphers you have written in Game Plan. Both encrypting and decrypting messages are supported. Encrypted messages are automatically saved to a `msgs` folder; messages to decrypt can be selected from this folder or typed manually. 

## Setup 
First, save a copy of `crypto_io.py` in the same folder as the cyphers you have written. 

Next, create a new subfolder named `\msgs`. This is where encrypted messages are stored and fetched from.  

Then, refactor the import calls on lines 6-9 to refer to your files and function definitions. Take line 6 for example:

    from YOUR_SHIFT_CYPHER_FILE import YOUR_SHIFT_DEF as shift_cypher

If your shift cypher is named `CeaserCypher.py`, and your encode function definition in that file is `def encode(message):`, you would rewrite line 6 to:

    from CeaserCypher import encode as shift_cypher`

**Note the .py extension on the file name is *not* included**. 

Line 6 now imports the `encode` function definition into `crypto_io`, and renames it as `shift_cypher`. Throughout `crypto_io`, all cypher functions are referred to by the names defined on lines 6-9; if you want to keep your original function names, or rename them to something else, you'll have to change every reference throughout `crypto_io` -- and be sure to avoid collisions.

## A Note On Import & Function Definitions 
Not all of the cyphers in Game Plan are set up to use function calls; some of them simply run the code, top to bottom. For these projects, obviously we can't import a function that hasn't been defined, so you'll need to refactor the cypher. Additionally, importing a file *runs* all the code in that file; in the case of function *definitions*, they are merely stored in memory; in the case of function *calls*, they'll be actually executed, and clutter up our user interface. So we have two reasons to refactor our earlier cyphers from linear programs to modular, function-based programs: to import those functions, and to remove clutter.  

Any code related to the functionality of the cypher should be moved into a new function defintion. Make sure that function **returns** a value, instead of printing it. 

Any code related to demoing the cypher with a hardcoded string, or by taking user input, should be moved into a `main()` function definition. To maintain the ability of the cypher to run independently of crypto_io, also include these two lines at the end of your file: 

    if __name__ == "__main__":
        main()

`__name__` is a special variable set by the Python environment at runtime. If the script is being run directly, `__name__` is set to `__main__`; if the script is being imported, `__name__` is set to the name of the script (aka module). With the above two lines, the cypher can run independently with the original input method, or can be called from crypto_io. 
