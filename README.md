# Garage-Management-system
video link:https://drive.google.com/file/d/1wt23UVLks3_asTV3mHfx6cXX3g4u0uyV/view?usp=sharing

Login to the respective trailhead account and navigate to the gear icon in the top right corner.

Click on the Developer console. Now you will see a new console window.

In the toolbar, you can see FILE. Click on it and navigate to new and create New apex class.

Name the class as “AmountDistributionHandler ”.














Code: 


public class AmountDistributionHandler {

    

    public static void amountDist(list<Appointment__c> listApp){

        list<Service_records__c> serList = new list <Service_records__c>();

        

        for(Appointment__c app : listApp){

            if(app.Maintenance_service__c == true && app.Repairs__c == true && app.Replacement_Parts__c == true){

                app.Service_Amount__c = 10000;

            }

            else if(app.Maintenance_service__c == true && app.Repairs__c == true){

                app.Service_Amount__c = 5000;    

            }

            else if(app.Maintenance_service__c == true && app.Replacement_Parts__c == true){

                app.Service_Amount__c = 8000;    

            }

            else if(app.Repairs__c == true && app.Replacement_Parts__c == true){

                app.Service_Amount__c = 7000;

            }

            else if(app.Maintenance_service__c == true){

                app.Service_Amount__c = 2000;

            }

            else if(app.Repairs__c == true){

                app.Service_Amount__c = 3000;

            }

            else if(app.Replacement_Parts__c == true){

                app.Service_Amount__c = 5000;

            }

            

    }

    }

}



trigger AmountDistribution on Appointment__c (before insert, before update) {

    

    if(trigger.isbefore && trigger.isinsert || trigger.isupdate){

        AmountDistributionHandler.amountDist(trigger.new);

        

    }


}
