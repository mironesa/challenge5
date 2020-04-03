# challenge5
// Created on Thu April 2 2020
int l_motor = 0;
int r_motor = 2;
int speed = 85; 
int slow = 20;
int target = 250;
int pause = 300;
int counter = 0;
int right_range = 2;
int middle_range = 1;
int tophat = 5;
int tophat_2 = 6;



void forwards() { // go forward 
	motor(l_motor,speed); 
	motor(r_motor,speed);
}

void backwards() { // go backwards
	motor(l_motor,-speed);  
	motor(r_motor,-speed);
}

void veer_left() { //veer left
	motor(r_motor,speed);
	motor(l_motor,slow);
}

void veer_right() { //veer right
	motor(r_motor,slow);
	motor(l_motor,speed);
}

void turn_left() { // turn left 
	motor(l_motor,-speed); 
	motor(r_motor,speed);
	
}

void wallrun() {
while (counter < 4) {
		
 if(analog(right_range) > 300) { // veer right
	   veer_right(); 
	   }
		
 if(analog(right_range) < 300) { // veer left
	   veer_left(); 
	   }
		
	   
 if(analog(middle_range) < 400) { //turn left 
	   turn_left();
	   }
	   
 if(analog(tophat_2) > 300) { 
	   counter ++ ;
	   forwards();
	   msleep(300);
	   printf("count = %d \n" ,counter); 
	   }
			
}
	
	ao();
	return 0;
}

int main() {	
	
	wallrun();
	
}
