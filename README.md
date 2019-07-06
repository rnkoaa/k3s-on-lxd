# Vagrant LXD creation

* `task --init`
* `task generate-ssh-keys`
* `task generate-jump-keys`
* `vagrant up`
* `task ansible-test`
* `task copy-ssh-jump-keys`
* `task base`
* `task prepare-lxd-users`
* Go to the server node and init lxd

    * See `lxd-init.yml` for answers for simple init
    * `lxd init`

* Create the k3s lxd profile using the command below
    * `task k3s-lxd-profile.yml`

* Create the k3s lxd profile using the command below
    * `task k3s-lxd-container.yml`
