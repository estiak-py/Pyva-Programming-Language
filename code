# =========================================
# Pyva Programming Language
# Python + Java Inspired Language
# Made by Estiak 😎
# =========================================

# ========= KEYWORDS =========

KEYWORDS = [
    "let",
    "print",
    "if",
    "else"
]

# ========= LEXER =========

def tokenize(code):

    tokens = []

    code = code.replace("{", " { ")
    code = code.replace("}", " } ")
    code = code.replace("(", " ( ")
    code = code.replace(")", " ) ")
    code = code.replace("=", " = ")

    words = code.split()

    for word in words:

        if word in KEYWORDS:
            tokens.append(("KEYWORD", word))

        elif word.isdigit():
            tokens.append(("NUMBER", word))

        elif word.startswith('"') and word.endswith('"'):
            tokens.append(("STRING", word))

        else:
            tokens.append(("IDENTIFIER", word))

    return tokens


# ========= PARSER =========

def parse(tokens):

    # Future AST system can go here
    return tokens


# ========= INTERPRETER =========

variables = {}

def run(tokens):

    i = 0

    while i < len(tokens):

        token = tokens[i]

        # ---------------------------
        # Variable Declaration
        # let x = 10
        # ---------------------------

        if token[1] == "let":

            name = tokens[i + 1][1]

            value_token = tokens[i + 3]

            value = value_token[1]

            # Remove quotes if string
            if value.startswith('"') and value.endswith('"'):
                value = value[1:-1]

            variables[name] = value

            i += 4

        # ---------------------------
        # Print Statement
        # print(name)
        # ---------------------------

        elif token[1] == "print":

            content = tokens[i + 2][1]

            # Variable print
            if content in variables:
                print(variables[content])

            else:

                # Remove quotes
                if content.startswith('"') and content.endswith('"'):
                    content = content[1:-1]

                print(content)

            i += 4

        else:
            i += 1


# ========= PYVA CODE =========

code = '''

let name = "Estiak"

print(name)

let age = 16

print(age)

print("Welcome to Pyva Language")

'''

# ========= MAIN =========

tokens = tokenize(code)

parsed = parse(tokens)

run(parsed)