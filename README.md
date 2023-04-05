# Demo interencing 
The demo counts cars and person on a looping video

```
helm fetch https://helm.ngc.nvidia.com/nvidia/charts/video-analytics-demo-0.1.8.tgz 

helm install video-analytics-demo video-analytics-demo-0.1.8.tgz  -n video-analytics --create-namespace -f values.yaml

NAME: video-analytics-demo
LAST DEPLOYED: Wed Apr  5 15:52:17 2023
NAMESPACE: video-analytics
STATUS: deployed
REVISION: 1
NOTES:
1. Get the RTSP URL by running these commands:
     NOTE: It may take a few minutes for the LoadBalancer IP to be available.
           You can watch the status of by running 'kubectl get --namespace video-analytics svc -w video-analytics-demo'
  export SERVICE_IP=$(kubectl get svc --namespace video-analytics video-analytics-demo -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
  echo http://$SERVICE_IP:80

2.Get the WebUI URL by running these commands:
  export ANT_NODE_PORT=$(kubectl get --namespace video-analytics -o jsonpath="{.spec.ports[0].nodePort}" services video-analytics-demo-webui)
  export NODE_IP=$(kubectl get nodes --namespace video-analytics -o jsonpath="{.items[0].status.addresses[0].address}")
  echo http://$NODE_IP:$ANT_NODE_PORT
  Disclaimer:
  Note: Due to the output from DeepStream being real-time via RTSP, you may experience occasional hiccups in the video stream depending on network conditions.

```
