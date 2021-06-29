# HITDAY22EX
package hit.day22;
/*Objectives of this exercise
 * How to make two threads work on a single object...
 * How to create two threads and assign two jobs
 * How to control threads
 */
public class ThreadDemo3 {
	public static void main(String[] args) {
		Thread t=Thread.currentThread();
		t.setName("muhaimeen");
		System.out.println("Reservation counter starting working..."+t.getName());
		
		ReservationCounter central=new ReservationCounter();
		
		Thread imran=new Thread(new BookingJob(central,1000),"imran");
		Thread taqi=new Thread(new BookingJob(central,500),"taqi");
		
		imran.start();
		taqi.start();
	}
}
class BookingJob implements Runnable{
	ReservationCounter central;int amt;
	public BookingJob(ReservationCounter central,int amt) {
		this.central=central;
		this.amt=amt;
	}
	@Override
	public void run() {
		central.bookTicket(amt);
		central.giveChange();
	}
}
class ReservationCounter{
	int amt;
	public void bookTicket(int amt) {
		Thread t=Thread.currentThread();
		this.amt=amt;
		String name=t.getName();
		System.out.println(name+" has come to book the ticket...");
		System.out.println(name+" brought...:"+amt);
	}
	
	public void giveChange() {
		Thread t=Thread.currentThread();
		String name=t.getName();
		System.out.println("Change given to...:"+name);
		System.out.println(name+" takes...:"+(amt-100));
	}
}


package hit.day22;
public class ThreadDemoSimple {
	public static void main(String[] args) {
		Thread t=new Thread(new Job());
		t.start();
	}
}
class Job implements Runnable{
	@Override
	public void run() {
		System.out.println("thread execution logic ");
	}
}

package hit.day22;
import java.util.Date;
public class ThreadDemo2 {
	public static void main(String[] args) throws Exception{
		VaccinationCenter vc=new VaccinationCenter();
		Thread t=Thread.currentThread();
		t.setName("shoiab");
		System.out.println(new Date());
		System.out.println("Before comming to class....");
		Thread kala=new Thread(new JobToKala(vc),"kala");
		kala.start();
		//vc.getToken();
		System.out.println("Take class.....for 7-9 Golden Batch...."+new Date());
	}	
}
class JobToKala implements Runnable{
	VaccinationCenter vc;
	public JobToKala(VaccinationCenter vc) {
		this.vc=vc;
	}
@Override
	public void run() {
		System.out.println("The job given to kala is executed from this method...");
		try{
			vc.getToken();
		}catch(Exception e) {
			e.printStackTrace();
		}
	}	
}
class VaccinationCenter {
	public void getToken() throws Exception{
		Thread t=Thread.currentThread();
		String name=t.getName();
		System.out.println(name+"...standing in queue for token....");
		Thread.sleep(10000);
		System.out.println("token received..."+new Date());
	}
}

package hit.day22;
/*Objectives of this exercise
 * How to make two threads work on a single object...
 * How to create two threads and assign two jobs
 * How to control threads
 */
public class ThreadDemo3 {
	public static void main(String[] args) {
		Thread t=Thread.currentThread();
		t.setName("muhaimeen");
		System.out.println("Reservation counter starting working..."+t.getName());
		
		ReservationCounter central=new ReservationCounter();
		
		Thread imran=new Thread(new BookingJob(central,1000),"imran");
		Thread taqi=new Thread(new BookingJob(central,500),"taqi");
		
		imran.start();
		taqi.start();
	}
}
class BookingJob implements Runnable{
	ReservationCounter central;int amt;
	public BookingJob(ReservationCounter central,int amt) {
		this.central=central;
		this.amt=amt;
	}
	@Override
	public void run() {
		central.bookTicket(amt);
		central.giveChange();
	}
}
class ReservationCounter{
	int amt;
	public void bookTicket(int amt) {
		Thread t=Thread.currentThread();
		this.amt=amt;
		String name=t.getName();
		System.out.println(name+" has come to book the ticket...");
		System.out.println(name+" brought...:"+amt);
	}
	
	public void giveChange() {
		Thread t=Thread.currentThread();
		String name=t.getName();
		System.out.println("Change given to...:"+name);
		System.out.println(name+" takes...:"+(amt-100));
	}
}
