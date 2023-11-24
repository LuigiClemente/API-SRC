### Install rbenv:


# Install dependencies
```bash
sudo apt-get update
sudo apt-get install -y git curl libssl-dev libreadline-dev zlib1g-dev build-essential
```

# Install rbenv
```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
```

# Install ruby-build as an rbenv plugin
```bash
git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
```

# Install rbenv-vars as an rbenv plugin (optional but recommended)
```bash
git clone https://github.com/rbenv/rbenv-vars.git ~/.rbenv/plugins/rbenv-vars
```
# Add rbenv to bash so that it loads every time you open a Terminal
```bash
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init --no-rehash -)"' >> ~/.bashrc
exec $SHELL
```

# Install Ruby 3.1.3:

```bash
rbenv install 3.1.3
```

# For `pg` gem:

```bash
sudo apt-get install libpq-dev
```

# For `rszr` gem:

```bash
sudo apt-get install libimlib2-dev
```

# Cloning Repository

```bash
git clone https://github.com/zammad/zammad.git
```
```bash
cd zammad
```

# Initializing Zammad

```bash
bundle config set --local without 'mysql'
```

```bash
bundle install
```

```bash
gem install rails
```

```bash
export PATH="$HOME/.rbenv/shims:$PATH"
```


```bash
sudo apt-get install -y nodejs
```
