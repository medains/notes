# Sed recipes

Search and replace in all files on mac

* `LC_ALL=C find ./ -type f -not -path "./.git/*" -exec sed -i '' -e 's/.parcel_shop./.address./g' {} \;`

# Processes

Avoid including grep in the output

* `ps aux | grep '[p]rocess'`

Discover which existing process is bound to a port

* `lsof -nP -iTCP:8080`

# Terminal

Clear terminal (including iterm2 scrollback)

* `printf '\033[2J\033[3J\033[1;1H'`

# SSH tunnelling

* `ssh -fN -L ${LOCALPORT}:${REMOTEHOST}:${REMOTEPORT} ${USER}@${TUNNELHOST}`
