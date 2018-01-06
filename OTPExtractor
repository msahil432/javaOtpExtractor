import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class OTPExtractor {

   public static void main( String args[] ) {
      String line = "OTP is : 223-33A";
      System.out.println(extractOtp(line));
   }
   
   public static boolean isOTP(String message){
        try{
            message = message.toLowerCase();
            if(message.contains("otp")){
                return true;
            }else if(message.contains("one time password")){
                return true;
            }else if(message.contains("verification code")){
                return true;
            }
        }catch (Exception e){
            e.printStackTrace();
        }
        return false;
    }

    private static final Pattern pattern = Pattern.compile(
            "(|^)[A-Z\\-0-9]{4,9}|(|^)\\d{2,4}-\\d{2,4}|(|^)\\d{4,8}", Pattern.MULTILINE);
    public static String extractOtp(String message){
        if(!isOTP(message)){
            return null;
        }
        String OTP = null;
        Matcher m = pattern.matcher(message);
        while (m.find()) {
            String temp = m.group(0);
            if(temp.contains("-")){
                String[] arr= temp.split("-");
                if(arr.length>2 || (arr[0].length()!=arr[1].length())){
                    continue;
                }
            }
            OTP = temp.replaceAll("-","");
        }
        return OTP;
    }
}
