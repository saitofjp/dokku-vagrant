# vagrantfile for Dokku 
 dokku is
 "Docker powered mini-Heroku. The smallest PaaS implementation you've ever seen."
 https://github.com/progrium/dokku

ちなみに、公式でもvagrantfile含まれてるから、こっちは勉強用

# startup & dokku install

    vargrant up

image after startup, dokku is automatically installed. as a provisioning

provisioning is use "vargrant ssh". if vargrant ssh does not work in windows, 
please run the provisioning command manually in the guest machine.

というか、vargrant ssh動かなくて、ゲストに入ってインストールしました。

# setting vhost
hostsに手で書くのだが、これが結局めんどい

# push
    git remote add dokku dokku@deploy.192.168.33.101.xip.io:node-js-sample
    git push dokku master

## push sample
     git clone git@github.com:heroku/node-js-sample.git
     cd node-js-sample
     git remote add dokku dokku@deploy.192.168.33.101.xip.io:node-js-sample
     git push dokku master

# config
    see vargrant file

