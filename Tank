public class Tank extends Sensors{
 
    private int level_low;
    private int level_medium;
    private int level_high;
    private int water_flow;

    public int getCode_dashboard(){
        return level_low + level_medium + level_high + water_flow;
    }

    public void setLevel_low(){
        level_low = getSensor1();
    }

    public void setLevel_medium(){
        level_medium = getSensor2();
    }

    public void setLevel_high(){
        level_high = getSensor3();
    }

    public void setWater_flow(){
        water_flow = getWater_pipe();
    }

    public void waterFlow(){
        int codeStatus = level_low + level_medium + level_high + water_flow;

        switch (codeStatus) {
            case 4: // 1111: level_low, level_medium, level_high, water_flow = ON
                System.out.println("Tanque status: Caixa d'água com 100% e recebendo água da rua");
                break;
            case 3: // 0111: level_low, level_medium, water_flow = ON
                System.out.println("Tanque status: Caixa d'água com 50%, recebendo água da rua");
                break;
            case 2: // 0010: level_low, water_flow = ON
                System.out.println("Tanque status: Atenção! Caixa d'água 10%, mas recebendo água da rua.");
                break;
            case 1: // 0001: Apenas water_flow = ON
                System.out.println("Tanque status: ALERTA! Caixa d'água vazia, mas recebendo água da rua!");
                break;
            case 0: // 0000: Nenhum sensor está ativo
                System.out.println("Tanque status: EMERGENCIA! Caixa d'água vazia, sem água da rua!");
                break;
            default:
                System.out.println("Tanque status: Erros nos sensores, verificar!");
                break;
        }

    }

    public void startTank(){
        setLevel_low();
        setLevel_medium();
        setLevel_high();
        setWater_flow();
        waterFlow();
    }

}
