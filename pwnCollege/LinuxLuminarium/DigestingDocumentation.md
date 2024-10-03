# Digesting Documentation

## 1. Learning from Documentation

*This level requires us to run the `/challenge/challenge` file with the `--giveflag` argument.<br>
A simple analogy to commands and arguments in terms of programming can be functions and parameters, with some parameters (arguments) being compulsory while others can be optional parameters that if nothing is mentioned, have default values that kick in.*

**Solution:**

`/challenge/challenge --giveflag`

## 2. Learning complex usage

*This level introduces the feature of commands which is that arguments of a command can have their own arguments, for which i will once again find a coding equivalent, it is simalar to keyword-aruguments in a function. In this problem, the solution involved giving the argument **flag** to the `--printfile` argument(keyword argument)*

**Solution:**

`/challenge/challenge --printfile flag`

## 3. Reading Manuals

*The `man` command takes any executable file as an argument and gives a description of it including the options that can be used with it. Using man on challenge gives the options for it, out of which one option had a description stating it will provide the **flag** if the argument given to it equals **940***

**Note:-**
1. **man** </br>
   The man command is used to get a detailed analysis of the features of a command, including itself. It ONLY takes the command name as an argument NOT the file path, relative ot full.</br>
   `man command_name`

**Solution:**

`man challenge` <br>
`/challenge/challenge --tzduml 940`

## 4. Searching manuals

*The manual of a command can be very long, in ushc cases there are specific keys that help with navigating the results of the `man` command. Using such methods on the result of `man challenge`, we can read through the options and find the correct one. Running the challenge file with the correct argument gives us the flag.*

**Note:-**
Scrolling - pgdw/pgup, arrow keys, mouse<br>
`/` to search<br>
`n` to go to the next result<br>
`N` to go to the previous result <br>
`?` to search backwards (i.e by matching suffix)<br>
`/b` to specify a word boundary in the search function (just an example, there are forms of implementing regex as well.)

**Solution:**

`man challenge`<br>
`/challenge/challenge --ewzxab`

## 5. Searching for manuals

*Using `man man` gave the manual page for the man command istelf, after extensive searching, in the Finding manual pages section, there is an option called `--wildcard` which takes an argument string and shows all pages that have the string in their name or description. I utilised this option for the man command with the argument **flag** and got the correct man page for challenge.*

**Solution:**

`man man` <br>
`man --wildcard flag` <br>
`/challenge/challenge --rmcdhx 414`

## 6. Helpful Programs

*Some programs dont have a dedicated man page but instead have a different way of explainignt their functionality, usually with the help of `--help` argument. using said argument on `/challenge/challenge` gives us 2 important options, `-g` to get the flag provided its argument is correct and `-p` to get the correct number that should be given as argument to `-g`. Using both, we get the flag.*

**Solution:**

`/challenge/challenge --help`<br>
`/challenge/challenge --p` <br>
`/challenge/challenge --g 64` <br>

## 7. Help for builtins

*Builtins are internal commands of the shell that can be run from anywhere and arent dependent on file path, they have no man page but rather their description can be obtained using another builtin `help`. Using `help` on the builtin command `challenge` gives us the necessary option as well as extra information to get the flag.*

**Solution:**

`help challenge` <br>
`challenge --secret 8cftTTym` 