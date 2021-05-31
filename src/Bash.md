- As the code snippet below, We would get the all val from `console.log`
  ```bash
  #!/bin/bash
  VAL=$(node app.js)
  ```
- The different we should know between bash and shell...[ref](https://stackoverflow.com/questions/5725296/difference-between-sh-and-bash)
- Same as NodeJS, we can use color-code to beauty the font...[ref](https://stackoverflow.com/questions/5947742/how-to-change-the-output-color-of-echo-in-linux)
  ```bash
  RED='\033[0;31m'
  NC='\033[0m' # No Color
  echo -e "This is ${RED}red${NC}"
  ```