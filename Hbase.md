# HBase

- There is an authorization process that can be setted up for the client 
- There is different mode of replication:  Master-Master, Master-slave and Cyclic

```HBase
# Creat a table, the syntaxe is : creat {Name=>'column1'}, {NAME=>'colomn2'}

creat 'UserInfo', {Name=>'username'}, {NAME=>'fullname'}, {NAME=>'homedir'}

# Add rows, the syntaxe is : put 'UserInfo', 'line_number', 'name column', value'

put 'UserInfo', 'r1', 'username', 'Celia'
put 'UserInfo', 'r2', 'username', 'Dehia'
put 'UserInfo', 'r3', 'username', 'Massi'
put 'UserInfo', 'r1', 'fullname', 'KHERFALLAH'
```
# See the data's there's

scan 'UserInfo'
scan 'UserInfo', {COLUMNS=>fullname'}
scan 'UserInfo', { COLUMNS => 'fullname', LIMIT => 3, FILTER => "ValueFilter( =, 'binaryprefix:hello_value2')" }

