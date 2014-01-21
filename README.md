# vim dictionary files for Opscode Chef


## VERSION

`Chef #=> 11.8.2`  
`Ohai #=> 6.20.0`

## Usage

### Clone to .vim/dict

```
$ mkdir -p ~/.vim/dict
$ git clone https://github.com/OpsRockin/opscode_chef.vim_dict.git ~/.vim/dict/opscode_chef.dict
```

### Use in vim

`:set dictionary+=~/.vim/dict/opscode_chef.dict/*.dict`

#### example for .vimrc

Toggle chef dictonary with `:ChefDicAdd` or `:ChefDicRem`.

```
" load_or remove chef_dict
command ChefDicAdd set dictionary+=~/.vim/dict/opscode_chef.dict/*.dict
command ChefDicRem set dictionary-=~/.vim/dict/opscode_chef.dict/*.dict
```

## Supports

### From source(rake task)

- platforms
- config options
- knife config options
- constants of provider
- all resouce names
- resouce options
- recipe methods
- DSL methods includes Chef::DSL::*
- Ohai automatic providers

### manually created(Todo: create rake task)

** _add_by_hand.dict **

- immediately


## Development

### requirements

-  a source code of the opscode chef
- ruby with bundler or activesupport
- rake



1. clone to opscode chef source to `./chef` and ohai source to `./ohai`
2. check out any version you need
2. bundle
3. edit `Rakefile` too add a new task
4. rake



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

