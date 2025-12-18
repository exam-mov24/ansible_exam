run

Host are set to [web]

```bash
# Test  --diff can be added for more info
ansible-playbook -C web.yml

# live run
ansible-playbook web.yml

# live run with tags
ansible-playbook web.yml --tags

```

```yaml
# change site if wanted
# in file change :
   web_index_url: "add_raw_format_here"

```