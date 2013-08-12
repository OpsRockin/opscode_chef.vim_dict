# Vim dict for Opscode Chef


## Chef::VERSION

`#=> 11.6.0`

## Usage

### Clone to .vim/dict

```
$ mkdir -p ~/.vim/dict
$ git clone https://github.com/OpsRockin/opscode_chef.vim_dict.git ~/.vim/dict/opscode_chef.dict
```

### Use in vim

`:set dictionary=~/.vim/dict/opscode_chef.dict/*.dict`


## Supports

### From source(rake task)

- platforms
- all resouce names
- resouce options
- recipe methods

### manually created(Todo: create rake task)

** _add_by_hand.dict **

- nothing
- immediately


## Licence and Author

LICENSE: MIT. (see LICENSE.txt)

Author: Yukihiko Sawanobori [[opslock.in](http://opsrock.in/), HiganWorks LLC]


Contributing
------------

1. Fork the repository on Github
2. Create a named feature branch (like `add_component_x`)
3. Write you change
4. Write tests for your change (if applicable)
5. Run the tests, ensuring they all pass
6. Submit a Pull Request using Github

