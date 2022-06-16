# requirment

package com.ReadingWriting;


import java.io.BufferedReader;
import java.io.File;  // Import the File class
import java.io.InputStreamReader;

public class GetFileInfo { 
  public static void main(String[] args) {
    File myObj = new File("C:\\DataDrive\\software\\eclipse\\eclipse-inst-jre-win64.exe");
    if (myObj.exists() && myObj.length() > (112*1048576)) {
      System.out.println("File name: " + myObj.getName());
      System.out.println("Absolute path: " + myObj.getAbsolutePath());
      System.out.println("Writeable: " + myObj.canWrite());
      System.out.println("Readable " + myObj.canRead());
      System.out.println("File size in bytes " + myObj.length());
      
      ProcessBuilder processBuilder=new ProcessBuilder();
      processBuilder.command("cmd.exe","/c","dir");
      try {
		Process process=processBuilder.start();
		StringBuilder builder=new StringBuilder();
		BufferedReader reader=new BufferedReader(
				new InputStreamReader(process.getInputStream()));
				
		
		String line;
		
		while((line=reader.readLine())!=null)
		{
		
			System.out.println(line);
		}
		
	} catch (Exception e) {
		// TODO: handle exception
	}
    } else {
      System.out.println("The file does not exist.");
    }
  }
}
