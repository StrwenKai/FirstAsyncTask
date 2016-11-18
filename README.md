# FirstAsyncTask

主要练习异步操作


1、在主程序中

public class MainActivity extends Activity {

	private Button operateButton=null;
	private Button sysoButton=null;
	
	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
		operateButton=(Button)findViewById(R.id.openNet);
		sysoButton=(Button)findViewById(R.id.SysOutIfo);
		operateButton.setOnClickListener(new operateListener());
		sysoButton.setOnClickListener(new sysoListener());
	}

	class operateListener implements OnClickListener{

		@Override
		public void onClick(View v) {
//		    OpenNetSrc netOperate=new OpenNetSrc();
//			netOperate.operate();
			
			FirstAsyncTask firstAsyncTask=new FirstAsyncTask();
			firstAsyncTask.execute();
		}
		
	}
	class sysoListener implements OnClickListener{

		@Override
		public void onClick(View v) {
			// TODO Auto-generated method stub
			System.out.println("输出信息");
		}
		
	}
	
	@Override
	public boolean onCreateOptionsMenu(Menu menu) {
		// Inflate the menu; this adds items to the action bar if it is present.
		getMenuInflater().inflate(R.menu.main, menu);
		return true;
	}

	@Override
	public boolean onOptionsItemSelected(MenuItem item) {
		// Handle action bar item clicks here. The action bar will
		// automatically handle clicks on the Home/Up button, so long
		// as you specify a parent activity in AndroidManifest.xml.
		int id = item.getItemId();
		if (id == R.id.action_settings) {
			return true;
		}
		return super.onOptionsItemSelected(item);
	}
}

2、新建一个类来模拟网络操作：
public class OpenNetSrc {
	public void operate(){
		
		try {
			Thread.sleep(5*1000);
			
			
		} catch (Exception e) {
			e.printStackTrace();
		}
		
	}

}

3、新建一个类实现异步操作
package com.practise.firstasynctask;

import android.os.AsyncTask;

public class FirstAsyncTask extends AsyncTask<Void, Void, Void> {

	@Override
	protected Void doInBackground(Void... params) {
	  OpenNetSrc netOperator=new OpenNetSrc();
	  netOperator.operate();
		return null;
	}

}
