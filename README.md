# pratik-code
import java.io.File;
import com.amazonaws.auth.BasicAWSCredentials;
import com.amazonaws.services.s3.AmazonS3Client;

public class uploadFile {

	static String link = "";

	static File file = new File("037.jpg");
	static String key =  file.getName();

	final static String accesskey = "AKIA323TEJZHEYE6EU6I";
	final static String secretkey = "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";
	final static String bucketname = "pratik1bucket";

	
	@SuppressWarnings("deprecation")
	private static AmazonS3Client s3 = new AmazonS3Client(new BasicAWSCredentials(accesskey, secretkey));
	
	public static void main(String[] args) {

		
		System.out.println("----file uploading---");

		try {
			s3.putObject(bucketname, key, file);
			} catch (Exception e) {
			e.printStackTrace();
			}
		System.out.println("----File uploaded----");

		System.out.println("\n\n----Get Object---");

		link = s3.getUrl(bucketname, key).toString();
		System.out.println("S3 Link: " + link);

	}
}
