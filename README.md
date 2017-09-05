# AviatrixSalesDemoApp
This repostiry is a sales application, that is used to demo some technical features of the Aviatrix Product.

## Prerequisites
Ensure that the infrastructure for the demo is set up. This can be done by using the [demo terraform script](https://github.com/AviatrixSystems/AviatrixSalesDemoInfra). 

If the instructions are followed carefully then the AviatrixSalesDemoApp should be cloned in to the EC2 instance named 'Client'. 

## Additional Set up 

### Scale Out Demo
* ssh in to the client EC2 instance and run the following commands - 
```
cd AviatrixSalesDemoApp
cd Demo_Webapp/
vi demo.py
```

* In the demo.py file, change the iperf command with the appropriate destination private IP, i.e, the private IP of the EC2 instance named 'Server'. Currently the IP address is an arbitrary one. Example -
 ```
 resp= subprocess.check_output (["iperf3", "-c", "192.168.1.235", "-V", "-b", "1024000000", "-t", "120"])
 ```
* ssh in to the ECS 'Server' instance and run the iperf server command - 
```
iperf3 -s
```
### Troubleshooting Demo
* ssh in to the client EC2 instance and run the following commands
```
cd AviatrixSalesDemoApp
cd Demo_Webapp/
cd templates
vi troubleshooting.html
```
* Add the appropriate destination IP, i.e, the IP of the EC2 named 'Server.(Currently the IP address is an arbitrary one.) 
* Ensure that the IP address still points to port 8080, and the port doesn't exist in the AWS Console so that it can be created during the demo. Example - 
```
<img src = "http://52.15.228.167:8080/likert.png" 

```

### Run the Application 
## To run the application in debugger mode
* Clone the repository

```
python demo.py
```
* Now go to your browser and open http://clientIPaddress:5000/ 
