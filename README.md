# Login-Page

import java.util.*;
import java.util.HashMap;
import java.util.Random;
import java.util.ArrayList;
class Main{
    public static void main(String[] args) {
        System.out.println("       ---------------------------------------------------------");
        System.out.print("      | Welcome to FlyHigh AirLines, Your Trusted Travel Partner! |");
        System.out.println("\n       ---------------------------------------------------------");
        Scanner sc = new Scanner(System.in);
        UserRegistration.registrationPanel(sc);
    }
}
class UserRegistration{
    public static void registrationPanel(Scanner sc){
        System.out.print("\nDo You have an account? (Yes/No/Exit) : ");
        String account = sc.nextLine();
        account=account.toLowerCase();
        switch(account){
            case "no":
                System.out.print("\n               --------------- Sign-Up ---------------\n");
                String name="";
                boolean validName=false;
                String userName=userName(sc,name,validName);
                String email="";
                boolean validEmailId=false;
                String userEmail=userEmail(sc,email,validEmailId);
                System.out.println("userEmail-Id : "+ userEmail);
                String mobileNumber="";
                boolean validMobileNumber=false;
                String userMobileNumber=userMobileNumber(sc,mobileNumber,validMobileNumber);
                System.out.println("userMobileNumber : "+ userMobileNumber);
                String generated=generate(sc);
                System.out.println(generated);
                userFinalProcess(sc);
            case "yes":
                break;
            case "exit":
                System.exit(0);
            default:
                 System.out.print("\nwrongly typed enter again...");
                 UserRegistration.registrationPanel(sc);
        }
    }
    public static String userName(Scanner sc,String name,boolean validName){
        System.out.print("\nEnter UserName : ");
        name=sc.nextLine();
        validName=isValidName(name);
        while(!validName){
            System.out.println("wrongly typed enter again... \nEnter UserName : ");
            name=sc.nextLine();
            validName=isValidName(name);
        }
        return name;
    }
    public static boolean isValidName(String name){
        if(name.length()==0){
            return false;
        }
        if(name.charAt(0)==' '){
            return false;
        }            
        for(int i=0;i<name.length();i++){
            if(name.charAt(0)>='0' && name.charAt(0)<='9'){
                return false;
            }
            else if(name==null){
                return false;
            }    
            else if(name.length()<3){
                return false;
            }
            else if(name.charAt(i)>=(char)33 && name.charAt(i)<=(char)47 || name.charAt(i)>=(char)91 && name.charAt(i)<=(char)96 ||
                name.charAt(i)>=(char)58 && name.charAt(i)<=(char)64 || name.charAt(i)>=(char)123 && name.charAt(i)<=(char)126){
                    return false;
                }
            }
            for(int i=1;i<name.length();i++){
                if(name.charAt(i)>='0' && name.charAt(i)<='9'){
                    return false;
                }
                if(name.charAt(0)>='a' && name.charAt(0)<='z'){
                    return false;
                }
                else if(name.charAt(0)>='A' && name.charAt(0)<='Z'){
                }
                else if(name.charAt(i)>='A' && name.charAt(i)<='Z'){
                    return false;
                } 
                if(name.charAt(i)>='A' && name.charAt(i)<='Z'){
                    if(name.charAt(i-1)==' '){
                    }
                    else{
                        return false;
                    }
                }
                else if(name.charAt(i)>='a' && name.charAt(i)<='z'){
                }
                if(name.charAt(i)==' '){
                    if(name.charAt(i+1)>='a' && name.charAt(i)<='z' ){
                        return false;
                    }
                }
            }
            int count=0;
            for(int i=name.length()-1;i>=0;i--){
                if(name.charAt(i)!=' '){
                    count++;
                }
                else{
                    break; 
                }
            }
            if(count<3){
                return false;
            }
            return true;
    }
    public static String userEmail(Scanner sc,String emailId,boolean validEmail){
        HashMap<String,String> map=new HashMap<>();
        map.put("gmail","@gmail.com");
        map.put("yahoo","@yahoo.com");
        map.put("outlook","@outlook.com");
        System.out.println("\nsign-in with gmail,yahoo or outlook \nEnter Domain Part : ");
        String mail=sc.nextLine();
        boolean ans=map.containsKey(mail);
        while(!ans){
            System.out.println("Not an account type again... \nEnter Domain Part : ");
            mail=sc.nextLine();
            ans=map.containsKey(mail);
        }
        System.out.println("\nsigning...");
        System.out.println("Enter Local Part : ");
        emailId=sc.nextLine();
        boolean answer=isValidEmailId(emailId);
        while(!answer){
            System.out.println("wrongly typed Local Part enter again...");
            emailId=sc.nextLine();
            answer=isValidEmailId(emailId);
        }
        return emailId +""+map.get(mail);
    }
    public static boolean isValidEmailId(String emailId){
        int countPeriods=1,countUnderScore=1,countHypen=1,countLower=1,countUpper=1,countNumber=1;
        if(emailId.length()<6){
            return false;
        }
        else if(emailId.equals("yahoo.com") || emailId.equals("gmail.com") || emailId.equals("outlook.com") || emailId.equals("yahoo") || emailId.equals("gmail") || emailId.equals("outlook") || emailId.equals("gmail.co.in") || emailId.equals("gmail.in") || emailId.equals("yahoo.co.in") || emailId.equals("yahoo.in") || emailId.equals("outlook.co.in") || emailId.equals("outlook.in") || emailId.equals("Gmail.com") || emailId.equals("GMAIL.com") || emailId.equals("Gmail.Com") || emailId.equals("Gmail.COM") || emailId.equals("GMAIL.Com") || emailId.equals("GMAIL.COM") || emailId.equals("Gmail.Co.in") || emailId.equals("Gmail.Co.In") || emailId.equals("Gmail.co.In") || emailId.equals("Gmail.co.in") || emailId.equals("GMAIL.co.in") || emailId.equals("GMAIL.CO.in") || emailId.equals("GMAIL.CO.In") || emailId.equals("GMAIL.CO.IN") || emailId.equals("GMAIL.co.IN") || emailId.equals("Gmail.co.IN") || emailId.equals("Yahoo.com") || emailId.equals("YAHOO.com") || emailId.equals("Yahoo.Com") || emailId.equals("Yahoo.COM") || emailId.equals("YAHOO.Com") || emailId.equals("YAHOO.COM") || emailId.equals("Yahoo.Co.in") || emailId.equals("Yahoo.Co.In") || emailId.equals("Yahoo.co.In") || emailId.equals("Yahoo.co.in") || emailId.equals("YAHOO.co.in") || emailId.equals("YAHOO.CO.in") || emailId.equals("YAHOO.CO.In") || emailId.equals("Yahoo.CO.IN") || emailId.equals("YAHOO.co.IN") || emailId.equals("Yahoo.co.IN") || emailId.equals("Outlook.com") || emailId.equals("OUTLOOK.com") || emailId.equals("Outlook.Com") || emailId.equals("Outlook.COM") || emailId.equals("OUTLOOK.Com") || emailId.equals("OUTLOOK.COM") || emailId.equals("Outlook.Co.in") || emailId.equals("Outlook.Co.In") || emailId.equals("Outlook.co.In") || emailId.equals("Outlook.co.in") || emailId.equals("OUTLOOK.co.in") || emailId.equals("OUTLOOK.CO.in") || emailId.equals("OUTLOOK.CO.In") || emailId.equals("OUTLOOK.CO.IN") || emailId.equals("OUTLOOK.co.IN") || emailId.equals("Outlook.co.IN")){
            return false;
        }
        else if(emailId.charAt(0)=='.' || emailId.charAt(0)=='-' || emailId.charAt(0)=='_'){
            return false;
        }
        else if(emailId.charAt(0)>='0' && emailId.charAt(0)<='9'){
            return false;
        }
        else if(emailId.charAt(0)>=(char)32 && emailId.charAt(0)<=(char)44 || emailId.charAt(0)>=(char)91 && emailId.charAt(0)<=(char)94 || emailId.charAt(0)>=(char)58 && emailId.charAt(0)<=(char)64 || emailId.charAt(0)>=(char)123 && emailId.charAt(0)<=(char)126 || emailId.charAt(0)==(char)47 || emailId.charAt(0)==(char)96){
            return false;
        }
        else if(emailId.charAt(emailId.length()-1)=='.' || emailId.charAt(emailId.length()-1)=='-' || emailId.charAt(emailId.length()-1)=='_' || emailId.charAt(emailId.length()-1)=='@'){
                return false;
        }
        for(int i=0;i<emailId.length();i++){
            if(emailId.charAt(i)==' '){
                return false;
            }
            else if(emailId.charAt(i)=='@'){
                if(emailId.charAt(i+1)>='a' && emailId.charAt(i+1)<='z'){
                    return false;
                }
            }
            else if(emailId.charAt(i)=='.' || emailId.charAt(i)=='-' || emailId.charAt(i)=='_'){
                for(int j=0;j<emailId.length();j++){
                    if(emailId.charAt(j)=='@'){
                        return false;
                    }
                }
            }
            else if(emailId.charAt(i)>=(char)32 && emailId.charAt(i)<=(char)44 || emailId.charAt(i)>=(char)91 && emailId.charAt(i)<=(char)94 || emailId.charAt(i)>=(char)58 && emailId.charAt(i)<=(char)64 || emailId.charAt(i)>=(char)123 && emailId.charAt(i)<=(char)126 || emailId.charAt(i)==(char)47 || emailId.charAt(i)==(char)96 || emailId.charAt(i)=='@'){
                return false;
            }
            else if(emailId.charAt(i)=='.' || emailId.charAt(i)=='-' || emailId.charAt(i)=='_'){
                if(emailId.charAt(i+1)=='.' || emailId.charAt(i+1)=='-' || emailId.charAt(i+1)=='_'){
                    return false;
                }
                else{
                    return true;
                }
            }
            else if(emailId.charAt(i)>='0' && emailId.charAt(i)<='9'){
                if(countNumber>=1 && countNumber<=5){
                    countNumber++;
                }
                else{
                    return false;
                }
            }
            else if(emailId.charAt(i)>='A' && emailId.charAt(i)<='Z'){
                if(countUpper>=1 && countUpper<=7){
                    countUpper++;
                }
                else{
                    return false;
                }
            }
            else if(emailId.charAt(i)>='a' && emailId.charAt(i)<='z'){
                if(countLower>=1 && countLower<=10){
                    countLower++;
                }
                else{
                    return false;
                }
            }
            else if(emailId.charAt(i)=='.'){
                if(countPeriods>=1 && countPeriods<=2){
                    countPeriods++;
                }
                else{
                    return false;
                }
            }
            else if(emailId.charAt(i)=='-'){
                if(countHypen>=1 && countHypen<=2){
                    countHypen++;
                }
                else{
                    return false;
                }
            }
            else if(emailId.charAt(i)=='_'){
                if(countUnderScore>=1 && countUnderScore<=2){
                    countUnderScore++;
                }
                else{
                    return false;
                }
            }
        }
        return true;
    }
    public static String userMobileNumber(Scanner sc,String mobileNumber,boolean validMobileNumber){
        HashMap<String,String> map=new HashMap<>();
    map.put("United States","(+1)");
    map.put("Canada","(+1)");
    map.put("India","(+91)");
    map.put("Brazil","(+55)");
    map.put("Indonesia","(+62)");
    map.put("Pakistan","(+92)");
    map.put("Nigeria","(+234)");
    map.put("Mexico","(+52)");
    map.put("South Africa","(+27)");
    map.put("Philippines","(+63)");
    System.out.println("Enter the country name : "); 
    String country=sc.nextLine();
    boolean ans=map.containsKey(country); 
    while(!ans){
        System.out.println("wrongly typed country name enter again...");
        country=sc.nextLine();
        ans=map.containsKey(country); 
    }
    System.out.println(country+" "+ map.get(country));
    System.out.println("Enter Mobile Number : ");
    mobileNumber=sc.nextLine();
    boolean answer=isValidMobNum(mobileNumber); 
    while(!answer){
        System.out.println("wrongly typed Mobile Number enter again..."); 
        mobileNumber=sc.nextLine();
        answer=isValidMobNum(mobileNumber); 
    }
    return map.get(country) +" : "+mobileNumber; 
    }
    public static boolean isValidMobNum(String mobileNumber){
        if(mobileNumber.length()==0){
            return false;
        }
        for(int i=0;i<mobileNumber.length();i++){
            if(mobileNumber.length()==10){ 
                if(mobileNumber.charAt(i)>='0' && mobileNumber.charAt(i)<='9'){ 
                }
                else{
                    return false;
                }
            }
            else{
                if(mobileNumber.length()>10 || mobileNumber.length()<10){
                    return false;
                }
            }
        } 
        return true;
    }
    public static String generate(Scanner sc){
        System.out.println("\nGenerate OTP or Create Password? (OTP/Password) : ");
        String type=sc.next();
        type=type.toLowerCase();
        if(type.equals("otp")){
            String generatedOtpPined=generatedOtpPin(sc);
            return generatedOtpPined;
        }
        else if(type.equals("password")){
            String generatedPassword=generatePassword(sc);
            return generatedPassword;
        }
        else{
            System.out.println("\nwrongly typed enter again...");
            generate(sc);
        }
        return "";
    }
    public static String generatedOtpPin(Scanner sc){
        String[] generatedOtp=generateOtp();
        System.out.println("OTP will be sent to your mobileNumber : " );
        String[] tempgeneratedOtp=new String[4];
        for(int i=0;i<tempgeneratedOtp.length;i++){
            tempgeneratedOtp[i]=generatedOtp[i];
            System.out.print(tempgeneratedOtp[i]+" ");
        }
        String[] otp=new String[4];
        boolean validOtp=false;
        String verified=userEnterOtp(sc,otp,validOtp,tempgeneratedOtp);
        return verified;
    }
    public static String[] generateOtp(){
        Random random=new Random();
        String[] randomNumber=new String[4];
        String[] randomlyGeneratedOtp=randomlyGenerateOtp(random,randomNumber);
        String[] temp=new String[4];
        for(int i=0;i<randomlyGeneratedOtp.length;i++){
            temp[i]=randomlyGeneratedOtp[i];
        }
        return temp;
    }
    public static String[] randomlyGenerateOtp(Random random,String[] randomNumber){
        int generatedNumber=0;
        String generatedNumbers="";
        for(int i=0;i<4;i++){
            generatedNumber=random.nextInt();
            if((generatedNumber%10)<0){
                generatedNumber=-(generatedNumber%10);
                generatedNumbers=String.valueOf(generatedNumber);
                randomNumber[i]=generatedNumbers; 
            }
            else{
                generatedNumber=generatedNumber%10;
                generatedNumbers=String.valueOf(generatedNumber);
                randomNumber[i]=generatedNumbers; 
            }
        }
        return randomNumber;
    }
    public static String userEnterOtp(Scanner sc,String[] otp,boolean validOtp,String[] tempgeneratedOtp){
        System.out.println("\nEnter 4-Digit OTP Number : ");
        for(int i=0;i<otp.length;i++){
            otp[i]=sc.next();
        }
        validOtp=isValidOtp(tempgeneratedOtp,otp);
        while(!validOtp){
            System.out.println("Invalid OTP...");
            System.out.println("\nResend OTP? (Yes/No) : ");
            String resend=sc.next();
            resend=resend.toLowerCase();
            if(resend.equals("yes")){
                String randomlyGeneratedOtp=generatedOtpPin(sc);
                return randomlyGeneratedOtp;
            }
            else{
                String generateOtpRandom=generate(sc);
                return generateOtpRandom;
            }
        }
        return "OTP will be Verified";
    }
    public static boolean isValidOtp(String[] tempgeneratedOtp,String[] otp){
        int j=0;
        for(int i=0;i<tempgeneratedOtp.length;i++){
            if(tempgeneratedOtp[i].equals(otp[j])){
                j++;
            }
            else{
                return false;
            }
        }
        return true;
    }
    public static String generatePassword(Scanner sc){
        String password="";
        String shownedPassword="";
        String shownReTypedPassword="";
        boolean validPassword=false;
        String userPassword=userPassword(sc,password,validPassword);
        int userPasswordLength=userPassword.length();
        System.out.println("\nuserPassword :");
        for(int i=0;i<userPasswordLength;i++){
            System.out.print("*");
        }
        System.out.print("\nAre You Want to View Password? (Yes/No) : ");
        String viewPassword=sc.next();
        viewPassword=viewPassword.toLowerCase();
        if(viewPassword.equals("yes")){
            shownedPassword=showPassword(userPassword);
            System.out.println(shownedPassword);
        }
        else{
        }
        String reTypePassword="";
        boolean validReTypePassword=false;
        String reTypedPassword=reTypePassword(sc,reTypePassword,validReTypePassword,userPassword);
        int reTypedPasswordLength=reTypedPassword.length();
        System.out.println("\nConfirm Password :");
        for(int i=0;i<reTypedPasswordLength;i++){
            System.out.print("*");
        }
        System.out.print("\nAre You Want to View confirm Password? (Yes/No) : ");
        String reTypedviewPassword=sc.next();
        reTypedviewPassword=reTypedviewPassword.toLowerCase();
        if(reTypedviewPassword.equals("yes")){
            shownReTypedPassword=showPassword(reTypedPassword);
        }
        else{
        }
        return shownReTypedPassword;
    }
    public static String userPassword(Scanner sc,String password,boolean validPassword){
        System.out.println("Enter password : ");
        password=sc.next();
        boolean ans=isValidPassword(password);
        while(!ans){
            System.out.println("wrongly typed password enter again...");
            password=sc.next();
            ans=isValidPassword(password);
        }
        return password;
    }
    public static String showPassword(String shownPassword){
        return shownPassword;
    }
    public static boolean isValidPassword(String password){
        int countNumber=1,countLower =1,countUpper=1,countSpecialChar=1;
        for(int i=0;i<password.length();i++){
            if(password.length()<8){
                return false;
            }
            if(password.charAt(i)==' '){
                return false;
            }
            else if(password.charAt(i)>='0' && password.charAt(i)<='9'){
                if(countNumber>=1 && countNumber<5){
                    countNumber++;
                } 
                else{
                    return false; 
                } 
            }
            else if(password.charAt(i)>='a' && password.charAt(i)<='z'){
                if(countLower>=1 && countLower<7){
                    countLower++;
                } 
                else{
                    return false;
                }
            }
            else if(password.charAt(i)>='A' && password.charAt(i)<='Z'){
                if(countUpper>=1 && countUpper<4){
                    countUpper++;
                }
                else{
                    return false;
                }
            }
            else if(password.charAt(i)>(char)33 && password.charAt(i)<(char)47 || password.charAt(i)>(char)91 && password.charAt(i)<(char)96 || password.charAt(i)>(char)58 && password.charAt(i)<(char)64 || password.charAt(i)>(char)123 && password.charAt(i)<(char)126){
                if(countSpecialChar>=1 && countSpecialChar<6){
                   countSpecialChar++;
                }
                else{
                    return false;
                }
            }
        } 
        return true;
    }
    public static String reTypePassword(Scanner sc,String reTypePassword,boolean validReTypePassword,String userPassword){
        System.out.println("\nconfrim password : ");
        String comfrimPassword=sc.next();
        boolean answer=isValidComfrimPassword(userPassword,comfrimPassword);
        while(!answer){
            System.out.println("wrongly typed confrim password enter again... ");
            comfrimPassword=sc.next();
            answer=isValidComfrimPassword(userPassword,comfrimPassword);
        }
        return comfrimPassword;
    }
    public static boolean isValidComfrimPassword(String userPassword,String comfrimPassword){
        int j=0;
        if(userPassword.length()>comfrimPassword.length()){
            return false;
        }
        for(int i=0;i<userPassword.length();i++){
            if(userPassword.charAt(i)==comfrimPassword.charAt(j)){
                j++;
            }
            else{
                return false;
            }
        }
        return true;
    }
    public static void userFinalProcess(Scanner sc){
        System.out.println("\nselect (SUBMIT/CANCEL) to complete the Sign-Up process : ");
        String registered=sc.next();
        registered=registered.toLowerCase();
        if(registered.equals("submit")){
            System.out.println("You are successfully Signed-Up...");
        }
        else if(registered.equals("cancel")){
            Scanner scanner= new Scanner(System.in);
            UserRegistration.registrationPanel(scanner);
        }
        else{
            System.out.println("wrongly typed enter again...");
            userFinalProcess(sc);
        }
    }
}
