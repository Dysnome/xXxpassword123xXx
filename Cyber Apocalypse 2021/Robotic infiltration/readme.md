```
$ rosbag info capture.bag 
path:        capture.bag
version:     2.0
duration:    4:26s (266s)
start:       Dec 31 1969 20:15:49.24 (4549.24)
end:         Dec 31 1969 20:20:15.37 (4815.37)
size:        326.8 MB
messages:    13309
compression: none [403/403 chunks]
types:       nav_msgs/Odometry       [cd5e73d190d741a2f92e81eda573aca7]
             sensor_msgs/PointCloud2 [1158d486dd51d683ce2f1be655c3c181]
             tf2_msgs/TFMessage      [94810edda583a504dfda3829e70d7eec]
topics:      odom              5323 msgs    : nav_msgs/Odometry      
             tf                5323 msgs    : tf2_msgs/TFMessage     
             tf_static            1 msg     : tf2_msgs/TFMessage     
             velodyne_points   2662 msgs    : sensor_msgs/PointCloud2


$ roscore
$ rosbag play capture.bag
$ rosnode list
-> /play
```