// Pumps.java
import java.time.Duration;
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class Pumps extends Sensors {

    private int water_pump1;
    private int water_pump2;

    private LocalDateTime startTimePump1;
    private LocalDateTime endTimePump1;
    private long Pump1TotalWorkedTime;

    private LocalDateTime startTimePump2;
    private LocalDateTime endTimePump2;
    private long Pump2TotalWorkedTime;

    public void setWater_pump1() {
        water_pump1 = getPump1();
        pump1WorkTime();
    }

    public void setWater_pump2() {
        water_pump2 = getPump2();
        pump2WorkTime();
    }

    public void pump1WorkTime() {

         DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss");


        if (water_pump1 == 1) {
            startTimePump1 = LocalDateTime.now();
            System.out.println("Bomba 1 ligada em: " + startTimePump1.format(formatter));
        } else {
            endTimePump1 = LocalDateTime.now();
            System.out.println("Bomba 1 desligada em: " + endTimePump1.format(formatter));
            calculateOperatingPump1Time();
        }
    }

    public void pump2WorkTime() {

        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss");


       if (water_pump2 == 1) {
           startTimePump2 = LocalDateTime.now();
           System.out.println("Bomba 2 ligada em: " + startTimePump2.format(formatter));
       } else {
           endTimePump2 = LocalDateTime.now();
           System.out.println("Bomba 2 desligada em: " + endTimePump2.format(formatter));
           calculateOperatingPump2Time();
       }
   }

    private long calculateOperatingPump1Time() {
        if (startTimePump1 != null && endTimePump1 != null) {
            Duration duration = Duration.between(startTimePump1, endTimePump1);
            long minutes = duration.toMinutes();
            Pump1TotalWorkedTime += minutes;
            System.out.println("Tempo total acumulado de Bomba 1: " + Pump1TotalWorkedTime + " minutos.");
            return Pump1TotalWorkedTime;
        }
        return Pump1TotalWorkedTime;
    }

    private long calculateOperatingPump2Time() {
        if (startTimePump2 != null && endTimePump2 != null) {
            Duration duration = Duration.between(startTimePump2, endTimePump2);
            long minutes = duration.toMinutes();
            Pump2TotalWorkedTime += minutes;
            System.out.println("Tempo total acumulado de Bomba 2: " + Pump2TotalWorkedTime + " minutos.");
            return Pump2TotalWorkedTime;
        }
        return Pump2TotalWorkedTime;
    }

    @Override
    public String getStatusMessage() {
        return String.format("Status das Bombas: Bomba 1 - %s | Bomba 2 - %s",
                water_pump1 == 1 ? "Ligada" : "Desligada",
                water_pump2 == 1 ? "Ligada" : "Desligada");
    }

    public void startPumps() {
        setWater_pump1();
        setWater_pump2();
        System.out.println(getStatusMessage());
        throw new UnsupportedOperationException("Not supported yet.");
    }

    
      
    
}
