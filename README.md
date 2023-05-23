# czn_infra

## Create the VM ci-server
cd vagrant
vagrant up

## Acces to he VM via ssh
vagrant ssh ci-server

## Apply permissions changes
vagrant provision ci-server
