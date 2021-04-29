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

```
transmission-create -t http://server:6969/announce -o output_file.torrent file_or_directory_to_share
```

The server url corresponds to the chihaya container url.

After that, you can add the torrent in the client's container transmission-web-service show above.

Finally you can share the torrent file to the other client and add it in his transmission-web-service to start downloading it from the corresponding peer.
