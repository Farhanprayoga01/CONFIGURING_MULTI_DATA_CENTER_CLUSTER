# CONFIGURING_MULTI_DATA_CENTER_CLUSTER
Konfigurasi multi data center cluster
##  jalankan command dibawah
    <img width="622" alt="197" src="https://github.com/Farhanprayoga01/CONFIGURING_MULTI_DATA_CENTER_CLUSTER/assets/143584670/00bea73f-b9d8-4b4f-a881-19a45f91f329">
    causal_clustering.discovery_type=LIST
    causal_clustering.minimum_core_cluster_size_at_formation=3
    causal_clustering.minimum_core_cluster_size_at_runtime=2
    causal_clustering.initial_discovery_members=192.168.18.197(IP1):5000,192.168.18.203(IP2):5000,192.168.18.214(IP3):5000
    causal_clustering.discovery_advertised_address=192.168.18.197:5000
    causal_clustering.transaction_advertised_address=192.168.18.197:6000
    causal_clustering.raft_advertised_address=192.168.18.197:7000

