pipeline {    
    agent {
        docker {
            image 'maven:3.9.9-amazoncorretto-23-alpine'
            args '-v /dev/bus/usb:/dev/bus/usb'  // For device access if needed
        }
    }

}
