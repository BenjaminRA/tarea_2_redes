# How to run

To run the enviroment, run the command:

```
docker-compose up
```

This will build and run the chihaya tracker server, as well as two peers that you can access with the following URLs:

```
http://localhost:9091/ => client
http://localhost:9098/ => client_2
```

# How to share a file

The `client` and `client_2` folders are linked to each container. To share a file you first have to copy the file you want to share, into the `torrents` folder.

Then, you need to create a the corresponding torrent file using the tool `transmission-create` provided by the software `Transmission`.

This can be achieved by using the client's command line by running:

```
docker exec -it container_name /bin/bash
```

After that, we can run the following command to create the torrent file, linked to the file or folder we want to share to the network.

```
transmission-create -t http://server:6969/announce -o output_file.torrent file_or_directory_to_share
```

The server url corresponds to the chihaya container url.

After that, you can add the torrent in the client's container transmission-web-service show above.

Finally you can share the torrent file to the other client and add it in his transmission-web-service to start downloading it from the corresponding peer.

# How to configure the server

A `chihaya.yaml` config file is mounted into the server container, and is located inside the folder `chihaya/config`.

# How to configure the server

Each client has its own `settings.json` config file, located inside `client/config`. This is applicable for both client and client_2.
