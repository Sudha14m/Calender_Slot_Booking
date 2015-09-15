import java.util.Scanner;

class duration
{
	String name;
    int start_hour, start_min;
    int end_hour, end_min;
    duration next;
    public duration(String name, int Start_Hour,int Start_Min,int End_Hour,int End_Min,duration next)
    {
		this.name=name;
		this.start_hour=Start_Hour;
		this.start_min=Start_Min;
		this.end_hour=End_Hour;
		this.end_min=End_Min;
	}
}
public class Calender 
{
	static int year, StartData,EndDate,month,StartHour,EndHour,StartMin,EndMin;
	static int []noOfDays={31,29,31,30,31,30,31,31,30,31,30,31};
	static duration head=null;
	static duration calender[] ;
	public static void main(String args [])
	{
		Scanner sc= new Scanner(System.in);
		boolean cont=true;
		calender=new duration[31];
		
		while(cont!=false)
		{	
			System.out.println("Your name please: ");
			String name=sc.nextLine();
			String[] months={"January","February","March","April","May","June","July","August","September","October","November","December"};
			System.out.println(" \nSelect an option\n1)Get an appointment for a time\n2)Show Free appointment time\n3)Cancel an appointment ");
			int n=sc.nextInt();
			sc.nextLine();
			if(n==1)
     		{
				System.out.println("Enter the date for appointment you need (in format: DD):");
				int dates=Integer.parseInt(sc.nextLine());
				if(IsValidDate_Month(dates))
				{
							 
					System.out.println("Enter the duration you need for appointment (format: HH:MM->hh:mm)");
					String duration=sc.nextLine();
					if(IsValidDuration(duration))
					{
						if(IsAllotmentAvailable(name, dates ,StartHour,EndHour,StartMin,EndMin))
						
							System.out.println(name+" , the appointment for your requested time is availale");
						else System.out.println("Sorry "+name+" , the appointment for your requested time is not availale");
					}
						
				}
	 				 
 			}
			else if(n==2)
			{
					 
					GetAppointment(calender);
			}
			else if(n==3)
			{
				 
				System.out.println("When was your appointment scheduled on:");
				int date=Integer.parseInt(sc.nextLine());
				if(Ispresent_Cancel(date,name))
				{
					delAtPos(date,name,pos);
					System.out.println(name+", Your appointment is successfully canceled. Thankyou");
				}
			}
			else
			{
				System.out.println("Wrong option selected.");
			}
			System.out.println("Do You Want To Continue(y/n)");
			if(sc.nextLine().equals("n"))
			 {	
				 System.out.println("\t\tThankyou");
				 cont=false;
		    }
	
		}
	}
 private static void delAtPos(int date, String cname, int pos2) 
 {
	 System.out.println(" position: "+pos2);
	 duration head1=calender[date-1];
	 duration current=head1;
		int n=0;
		duration temp=current.next;
		while(n<pos-1)
		{
			current=current.next;
			temp=temp.next;
			n++;
		}
		 current.next=temp.next;
		
}
static int pos=-10;
	private static boolean Ispresent_Cancel(int date, String cname)
	{
		duration head1=calender[date-1];
		int i=0;
		if(head1!=null)
		{
			duration current=head1;
			while(current!=null)
			{
				if(current.name.equals(cname))
				{
					pos=i;
					 return true;
				}
				current=current.next;
			i++;
			}
		}	
		System.out.println("there is no appointment with name"+cname);
		
		return false;
	}
	private static void GetAppointment(duration[] calender2) 
	{
		for(int i=1;i<=calender2.length;i++)
		{
			
			duration head1=calender2[i-1];
			 
			if(head1!=null)
			{
				System.out.println("\nAppointments alloted for  date: "+i);
				duration current=head1;
				while(current!=null)
				{	
				 
					System.out.println(current.start_hour+":"+current.start_min+"->"+current.end_hour+":"+current.end_min );
					current=current.next;
					 
				}
			}
			else System.out.print(" ");
		}
	}
	static duration end=null;
	private static boolean IsAllotmentAvailable(String name ,int date , int Start_Hour, int End_Hour, int Start_Min, int End_Min)
	{
		head=calender[date-1];
		duration temp=null;
		duration current=head;
		if(head==null)
		{
			head= new duration(name, Start_Hour, Start_Min, End_Hour, End_Min, null);
			end=head;
			calender[date-1]=head;
			return true;
		}
		else
		{
			duration appointment=new duration(name, Start_Hour, Start_Min, End_Hour, End_Min,temp);	
			while((current.next!=null)&&((Start_Hour*60)+Start_Min)>((current.end_hour*60)+current.end_min))
			{
				 current=current.next;
			}
			if(current.next!=null) 
			{
				temp=current.next;
				if((temp.start_hour*60)+temp.start_min>=(End_Hour*60)+End_Min)
				{
					current.next=appointment;
					appointment.next=temp;
					return true;
				}
			}
			else
			{
				if((current.end_hour*60)+current.end_min<=(Start_Hour*60)+Start_Min)
				{
				current.next=appointment;
				end=appointment;
				return true;
				}
				else
					return false;
			}
		}
		return false;
	}
	private static boolean IsValidDuration(String duration)
	{
		try
		{
			String start=(duration.split("->"))[0];
			String end=(duration.split("->"))[1];
			StartHour=Integer.parseInt((start.split(":"))[0]);
			EndHour=Integer.parseInt((end.split(":"))[0]);
			StartMin=Integer.parseInt((start.split(":"))[1]);
			EndMin=Integer.parseInt((end.split(":"))[1]);
	 
			if(StartHour>=9&&EndHour<=22&&StartMin>=00&&EndMin<=60&&StartHour<=EndHour)
			{
				return true;
			}
			else
			{
				System.out.println("Wrong Duration, Check for the duration");
				return false;
			}
		}
		catch (Exception e)
		{
			System.out.println("Wrong Format of the duration, Please enter the dates in the format format: HH:MM->hh:mm");
		}
			return false;
	}
	private static boolean IsValidDate_Month(int dates) 
	{
		try 
		{
			if((dates>0&&dates<=30))
			{
				return true;
			}
			else
			{
				System.out.println("Check the date for the corresponding month");
				return false;
			}
			
		} 
		catch (Exception e)
		{
			System.out.println("Wrong Format of the date, Please enter the dates in the format DD->DD");
		}
			return false;
	}
}
