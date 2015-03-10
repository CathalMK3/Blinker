#
#!/bin/sh

gpio=$1
time=$2

if[[ -z $1 || -z $2 ]]
	then
		echo ./flash.sh [gpio] [delay_time]
		echo Please enter all inputs
		exit 1
else
		echo You\'ve enter $1 $2
fi

#sudo sh -c "echo $gpio > /sys/class/gpio/export"
sudo chown -v root:root /sys/class/gpio/export
echo $gpio > /sys/class/gpio/export

path=/sys/class/gpio/gpio$gpio #set path variable
sudo chown - Rv root:root $path/

echo out > $path/direction
# blink for 50 times
