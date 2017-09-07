# admin-tigre.iul.lab
Set of imanagement scripts for the SO server at ISCTE-IUL

## User management
You can perform the following operations inside the ./users directory   

You may execute the following command to avoid encoding problems
    export LC_ALL="pt_PT.UTF-8"

Add new users to the group "so", based on a list of users    
    sudo ./append_users.sh alunos_test.txt [so]

Reseting the password of a student 
    sudo ./reset_password.sh fmmb@iscte-iul.pt a88888
   
Delete all the accounts 
    cat /etc/passwd | awk -F':' '/^a[0-9]/ {print $1}' | while read user; do
      echo deluser $user --remove-home
    done
   
Adding students to a new group that does no exist yet 
    sudo addgroup pcl
    sudo ./append_users.sh alunos_pcl.txt pcl
   
Use ASCII only and remove special characters 
    iconv -f UTF-8 -t 'ASCII//TRANSLIT'
   
Analyse running processes 
    ps -eo pcpu,pid,user,args --no-headers| sort -t. -nk1,2 -k4,4 -r |head -n 5


