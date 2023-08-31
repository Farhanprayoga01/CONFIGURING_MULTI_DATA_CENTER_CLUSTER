# CONFIGURING_MULTI_DATA_CENTER_CLUSTER
Konfigurasi multi data center cluster
## Siapkan beberapa Mesin dimana sudah ada neo4j yang terinstalasi didalamnya (saya buat contoh dengan 3 mesin dengan ipaddress berbeda yang sudah saya buat)

## Langkah selanjutnya ikuti command dibawah dengan contoh visual pada gambar berikut:
<img width="622" alt="197" src="https://github.com/Farhanprayoga01/CONFIGURING_MULTI_DATA_CENTER_CLUSTER/assets/143584670/00bea73f-b9d8-4b4f-a881-19a45f91f329">
    
    causal_clustering.discovery_type=LIST
    causal_clustering.minimum_core_cluster_size_at_formation=3
    causal_clustering.minimum_core_cluster_size_at_runtime=2
    causal_clustering.initial_discovery_members=192.168.18.197(IP1):5000,192.168.18.203(IP2):5000,192.168.18.214(IP3):5000
    causal_clustering.discovery_advertised_address=192.168.18.197:5000
    causal_clustering.transaction_advertised_address=192.168.18.197:6000
    causal_clustering.raft_advertised_address=192.168.18.197:7000
### Ketiga mesin tersebut belum menjadi multi data center karena masih tidak dapat menulis dan membaca antara satu sama lain. Hal ini dikarenakan tidak terkonfigurasi oleh server side routing.

## Langkah selanjutnya yaitu kita harus mengkonfigurasi server side routing nya juga di dalam neo4j.conf ini dengan cara dibawah:
<img width="311" alt="SSR" src="https://github.com/Farhanprayoga01/CONFIGURING_MULTI_DATA_CENTER_CLUSTER/assets/143584670/77f3f29b-aa97-4636-ac1a-4b131dccd325">

    #Server Side Routing
    dbms.routing.enabled=True
    dbms.routing.listen_address=0.0.0.0:7688
    dbms.routing.advertised_address=192.168.18.197(sesuai IP setiap mesin yang mau dicluster):7688
### Lakukan langkah ini terhadap configurasi dari setiap mesin yang kita cluster. 

### Dan jangan lupa bahwa listen dan advertised address diconfig seperti ini :
<img width="353" alt="listen address dan advertised address" src="https://github.com/Farhanprayoga01/CONFIGURING_MULTI_DATA_CENTER_CLUSTER/assets/143584670/75e101cb-49fd-46cf-96be-2584f626ef46">


### *Tambahan, jika kita mau menjadikan mode salah satu mesin kita menjadi read replica dengan cara dibawah:
<img width="134" alt="Screenshot 2023-08-31 124621" src="https://github.com/Farhanprayoga01/CONFIGURING_MULTI_DATA_CENTER_CLUSTER/assets/143584670/1f30b7f9-e5d3-4844-bc89-5e3fd6d5d6b4">
    
    #ROLE
    dbms.mode=READ_REPLICA





## Configurasi telah selesai, dan kita dapat start neo4j dari direktori 
    bin/neo4j start





