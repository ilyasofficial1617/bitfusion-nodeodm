# build the image locally
docker build -t nodeodmbitfusion -f Dockerfile.gpu.bitfusion .

# run it with existing nodeodm network
# repeat this with different name but the same network
docker run -d --name nodebf1 --rm --network="webodm_default" nodeodmbitfusion 
# inside WebODM, add more node, nodebf1:4000

# alternatively, this expose port to all, perfect for debugging
# left port is the outside port, the right side is for the app
docker run -d nodeodmbitfusion -p 4000:3000

# webodm start script
# default nodes for number of nodes
./webodm.sh --default-nodes 0 --port 320002 start 