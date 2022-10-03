# Tools - Restore

David Williamson @ Varilink Computing Ltd

------

A tool for restore from backup operations for the services deployed via Varilink's [Services - Ansible](https://github.com/varilink/services-ansible) repo.

This tool requires access to the database for the Bacula Director catalog. Since this tool is used on the desktop, if that database is local to the Bacula Director and so only exposed to the localhost on the Bacula Director host then it's necessary to temporarily expose that database on the Bacula Director host's external interface. The playbook `expose-backup-database.yml` is provided in the [Services - Ansible](https://github.com/varilink/services-ansible) repo for that purpose as is the playbook `cover-backup-database.yml` for removing that access again.

Recreate catalog from a single volume:

```bash
docker-compose run --rm restore volumes Catalogue-0200
```

Recreate catalog from multiple volumes:

```bash
docker-compose run --rm restore volumes Monthly_Off-Site-0330\|Monthly_Off-Site-0180\|Monthly_Off-Site-0363\|Monthly_Off-Site-0677\|Monthly_Off-Site-0296\|Monthly_Off-Site-0683
```

```
bscan: butil.c:151-0 Volume name or names is too long. Please use a .bsr file.
```
