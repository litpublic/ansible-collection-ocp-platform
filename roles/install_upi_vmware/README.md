# Install UPI VMware Role

Provides a scaffold for deploying OpenShift on vSphere via the UPI workflow. The current implementation is a guarded placeholder: you must opt in before the diagnostic tasks run.

## Usage

```yaml
- hosts: localhost
  gather_facts: false
  roles:
    - role: litpublic.ocp_platform.install_upi_vmware
      vars:
        lit_experimental_acknowledge: true
        vsphere_vcenter: vcenter.example.com
        vsphere_username: administrator@vsphere.local
        vsphere_password: "{{ lookup('env', 'VSPHERE_PASSWORD') }}"
        template_name: rhcos-template
        template_ova_url: https://mirror.openshift.com/.../ova
```

## Variables

- `lit_experimental_acknowledge`: must be `true` to bypass the safety fail (default: `false`)
- `vsphere_vcenter`, `vsphere_username`, `vsphere_password`: credentials for the target vCenter
- `vsphere_datacenter`, `vsphere_cluster`, `vsphere_datastore`, `vsphere_network`, `resource_pool`, `folder`: location settings for new VMs
- `template_ova_url`, `template_name`: RHCOS OVA source and resulting template name
- `ignition_bootstrap`, `ignition_master`, `ignition_worker`: local paths to ignition files
- `masters`, `workers`, `vm_cpu`, `vm_memory_mb`, `vm_disk_gb`: sizing inputs for created nodes
- `dns_servers`, `gateway`, `netmask`, `domain`: network settings applied to the provisioned VMs
