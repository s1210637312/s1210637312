import java.util.Calendar;

public class MyCalendar1 {

	public static void main(String[] args) {
		//実行時の日付/時刻情報を持つカレンダーインスタンス作成(ex 2021/01/08 22:00:00)
		Calendar cal=Calendar.getInstance();
		//インタンスの持つ日付情報を1日に変更(ex 2021/01/01 22:00:00)
		cal.set(Calendar.DATE, 1);
		//DAY_OF_WEEKでその日の曜日を返す2021/01/01は金曜なので6
		//（日曜:1,月:2,火:3,,,,土:7）
		//カレンダー的な最初のブランクの数は以下の式で表せる(1日が金なら空白は日、月、火、水、木の５個)
		int beforeBlank=cal.get(Calendar.DAY_OF_WEEK)-1;
		//その月が何日まであるかは以下のメソッドで求められる(1月は31日)
		int daysCount=cal.getActualMaximum(Calendar.DAY_OF_MONTH);
		//ブランクと日数分ループを回す
		for(int i=0;i<beforeBlank+daysCount;i++) {
			String str="";//ブランクは空文字
			//最初のブランク分すぎたら日付
			if(i>=beforeBlank) {
				//カウンター変数iから求める実際の日付
				int date=i+1-beforeBlank;
				str=String.valueOf(date);
			}
			//４文字分のスペースを使って描画
			System.out.printf("%4s", str);
			//7個出力したら改行
			if((i+1) % 7 == 0) {
				System.out.println();
			}
		}
		System.out.println();
	}
}
