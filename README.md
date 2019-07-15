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

On Control host add this command

    lxc remote add vagrant 192.168.33.10
     lxc launch ubuntu:x --config=user.user-data="$(cat user-data.yml)"

On User machine

`ansible-playbook -i hosts.yml k3s-yml`


## Known Issues
- Master not starting due to overlay Issues [similar issue here](https://github.com/docker/for-linux/issues/475)

- https://github.com/rancher/k3s/blob/master/k3s.service
