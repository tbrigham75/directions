1.  Go to Projects:  OpenShift-Storage > Pods > rook-ceph-tools (scroll all way to bottom)
2.  Open Terminal
3.  sh-4.4$ ceph status
  cluster:
    id:     9d783725-will-have-id-number-this-is-fake-a7878dff7878306
    health: HEALTH_OK
 
  services:
    mon: 3 daemons, quorum a,e,l (age 16h)
    mgr: a(active, since 16h)
    mds: 1/1 daemons up, 1 hot standby
    osd: 9 osds: 9 up (since 16h), 9 in (since 5w)
 
  data:
    volumes: 1/1 healthy
    pools:   4 pools, 265 pgs
    objects: 14.67M objects, 1.6 TiB
    usage:   4.8 TiB used, 13 TiB / 18 TiB avail
    pgs:     265 active+clean
 
  io:
    client:   64 KiB/s rd, 418 KiB/s wr, 3 op/s rd, 10 op/s wr
	
	