while True:  # Infinite loop to keep showing the menu until the user exits
    print("\n welcome to hacker cipher app: \n 1_encrypt a message \n 2_decrypt \n 3_exit")
    choice = input("choose an option (1/2/3): ")

    if choice == "1":  # Encrypting a message
        from getpass import getpass  # hides the input so nobody sees your secret key
        try:
            key = int(getpass("what is ur secret key? "))  # user inputs encryption key
        except ValueError:  # error if they type letters instead of a number
            print("that's not a number! try a number!")
            continue

        rletter = getpass("say something: ")  # hides the message input too
        letter = rletter.lower()  # convert message to lowercase
        result = ""  # empty string to store the encrypted message

        for i in letter:  # loop through every character in the message
            if i == " ":  # keep spaces as they are
                result += " "
            elif i == "!":  # keep ! as it is
                result += "!"
            elif i == "?":  # keep ? as it is
                result += "?"
            else:
                # shift the letter using Caesar cipher logic
                let = chr((ord(i) - ord("a") + key) % 26 + ord("a"))
                result += let  # add the encrypted letter to result

        print(f"Encrypted: {result} ")  # show encrypted message

    elif choice == "2":  # Decrypting a message
        from getpass import getpass
        try:
            key = int(getpass("what is ur secret key? "))  # user enters decryption key
        except ValueError:
            print("that's not a number! try a number!")
            continue

        rletter2 = input("what do u want to decrypt: ")  # get the encrypted message
        letter2 = rletter2.lower()
        result = ""  # empty string to store the decrypted message

        for i in letter2:  # loop through every character
            if i == " ":  # keep spaces
                result += " "
            elif i == "!":  # keep !
                result += "!"
            elif i == "?":  # keep ?
                result += "?"
            else:
                # reverse the Caesar shift to get original letter
                let2 = chr((ord(i) - ord("a") - key) % 26 + ord("a"))
                result += let2

        print(result)  # show decrypted message

    elif choice == "3":  # Exit the app
        print("you have exited the program!")
        break

    else:
        print("choice not available! try again!")  # if user types an invalid choice
