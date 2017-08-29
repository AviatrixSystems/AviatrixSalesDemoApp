# AviatrixSalesDemoApp
This repostiry is a sales application, that is used to demo some technical features of the Aviatrix Product.

## Prerequisites
Ensure that the infrastructure for the demo is set up. This can be done by using the [demo terraform script](https://github.com/AviatrixSystems/AviatrixSalesDemoInfra). 

If the instructions are followed carefully then the AviatrixSalesDemoApp should be cloned in to the EC2 instance named 'Client' in us-east-1. 

## Additional Set up 

### Scale Out Demo

* In the demo.py file, change the iperf command in line 28 with the appropriate destination IP, i.e, the IP of the EC2 instance named 'Server' in us-west-1. Currently the IP address is an arbitrary one. Example -
 ```
 resp= subprocess.check_output (["iperf3", "-c", "192.168.1.235", "-V", "-b", "1024000000", "-t", "120"])
 ```

* In the ECS 'Server' instance, run the iperf server command - 
```
iperf3 -s
```

### Troubleshooting Demo

* Go to Demo_Webapp > templates > troubleshooting.html.
* Replace line 555 with the appropriate destination IP, i.e, the IP of the EC2 named 'Server' is us-west-1. Currently the IP address is an arbitrary one. 
* Ensure that the IP address still points to port 8080, and the port doesn't exist in the AWS Console so that it can be created during the demo. Example - 
```
<img src = "http://52.15.228.167:8080/likert.png" 

```

### Run the Application 
## To run the application in debugger mode
Clone the repository

```
export FLASK_APP=./demo.py
export FLASK_DEBUG=1
python -m flask run
```

