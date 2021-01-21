# Jenkins chart for Kubernetes

This is a Helm chart that installs Jenkins.

I use ArgoCD to deploy this into a test cluster, but it should be installable by CLI Helm (though I haven't tested that).

There is nothing special about it. It has a dependency on the official Helm chart and is customised in `values.yml`.'

One of the customisations is to enable `persistence`. I use K3s and it provides Rancher's Local Path Provisioner. With `persistence` enabled, the Jenkins chart grabs a PV and PVC that uses that to persist config and job details across updates and restarts.

**_NOTE:_** Pay attention to the `templates` directory. It contains a Traefik Ingressroute definition, and a NFS PV with associated PVC.

They are unlikely to work with whatever your local cluster set up is.
