# Ansible - Download Example

To download a file to your `/tmp` perform the following:

```
# - name: Download Powerchute from APC
#   ansible.builtin.get_url:
#     url: https://download.schneider-electric.com/files?p_Doc_Ref=SPD_ARAJ-PCNS50LNX_EN&p_enDocType=Software+-+Release&p_File_Name=pcns500Linux-x86-64.tar.gz
#     dest: /tmp/pcns500Linux-x86-64.tar.gz
#     mode: 0644
#     force: true
#   when: powerchute_download.stat.exists is false
```


