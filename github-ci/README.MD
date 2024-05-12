# Copy files to vps

```yml
# https://stackoverflow.com/questions/68412832/github-actions-copy-files-to-vps

- name: Copy dist to VPS
    uses: appleboy/scp-action@master
    with:
    host: ${{ secrets.SSH_HOST }}
    username: ${{ secrets.SSH_USER }}
    port: ${{ secrets.SSH_PORT }}
    key: ${{ secrets.SSH_KEY }}
# Selecting all folders except "node_modules"
    source: ".,!node_modules"
# The path is based on the directory where the user logged into the server starts
    target: "~/app/gobarber-backend"
```

# ssh to vps

https://github.com/appleboy/ssh-action

