 bot Api <2081184462:AAEY5pxfawFaY1XiAxCQcRLfWEU8PVDxFfk>
 /*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

import javax.microedition.midlet.*;
import javax.microedition.lcdui.*;
/**
 * @ProtectChannelBot user
 */
public class CalculatorMidlet extends MIDlet implements CommandListener
{
    private Display d;
    private Form f;
    private TextField tf1,tf2;
    private ChoiceGroup cg;
    private StringItem si;
    private Command exit,calculate;
    private int a,s,m,div;


    public CalculatorMidlet()
    {
        d=Display.getDisplay(this);
        f=new Form("Calculator");


        exit=new Command("Exit",Command.EXIT,0);
        calculate=new Command("Calculate",Command.SCREEN,0);
        f.addCommand(exit);
        f.addCommand(calculate);
        f.setCommandListener(this);


        tf1=new TextField("Number1","",4,TextField.NUMERIC);
        tf2=new TextField("Number2","",4,TextField.NUMERIC);
        f.append(tf1);
        f.append(tf2);

        si=new StringItem("Result","");
        f.append(si);

        cg=new ChoiceGroup("Operation",List.EXCLUSIVE);
        a=cg.append("Add", null);
        s=cg.append("Subtract", null);
        m=cg.append("Multiply", null);
        div=cg.append("Divide", null);
        f.append(cg);





    }
    public void startApp()
    {
        d.setCurrent(f);
    }

    public void pauseApp()
    {
    }

    public void destroyApp(boolean unconditional)
    {
    }
    public void commandAction(Command cmd,Displayable disp)
    {
      if(cmd==exit)
      {
          destroyApp(true);
          notifyDestroyed();
       }
      if(cmd==calculate)
      {
          calc();
          d.setCurrent(f);

      }
    }
    private void calc()
    {
       int n1,n2,n;
       n1=Integer.parseInt(tf1.getString());
       n2=Integer.parseInt(tf2.getString());
       if(cg.getSelectedIndex()==a)
       {
         n=n1+n2;
         si.setText(String.valueOf(n));
       }
        if(cg.getSelectedIndex()==s)
       {
         n=n1-n2;
         si.setText(String.valueOf(n));
       }
        if(cg.getSelectedIndex()==m)
       {
         n=n1*n2;
         si.setText(String.valueOf(n));
       }
        if(cg.getSelectedIndex()==div)
       {
         n=n1/n2;
         si.setText(String.valueOf(n));
       }
       
    }
}
