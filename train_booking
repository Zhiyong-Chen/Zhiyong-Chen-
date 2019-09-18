#include <iostream>
#include <iomanip>
#include <fstream>
#include <ctime>
using namespace std;
int seat[6][3];
class Train {
	int number; //train number
	int seats_1;//車廂1 (未完成)
	int seats_2;// 車廂2 (未完成) 
	int seats_3;//車廂3 (未完成) 
public:
	Train(int i, int j, int k, int l)
	{
		number = i; seats_1 = j;
		seats_2 = k; seats_3 = l;
	}
	int getnum(void)
	{
		return number;
	}
	int getseats_1(void)
	{
		return seats_1;
	}
	int getseats_2(void)
	{
		return seats_2;
	}
	int getseats_3(void)
	{
		return seats_3;
	}
};
class Reservation :public Train
{
	int bkd_1;// seats reserved in 1st class
	int bkd_2;//seats reserved in 2nd class
	int bkd_3;// seats reserved in 3rd class
public:
	int i, j, k, l;
	Reservation(int i, int j, int k, int l) :Train(i, j, k, l)
	{
		bkd_1 = bkd_2 = bkd_3 = 0;
	}
	void book(int train,char type, int num);
	void cancel(int train, char type, int num);
	void disp_status(void);
};
void Reservation::book(int train_num,char type, int seats)
{
	switch (type)
	{
	case'1':
		seat[train_num - 1][0] -= seats;
		seat[train_num - 1][2] -= seats;
		/*bkd_1 += seats;
		bkd_3 += seats;*/
		/*cout << seat[train_num - 1][0] << endl;
		cout << seat[train_num - 1][2] << endl;*/
		break;
	case'2':
		seat[train_num - 1][1] -= seats;
		seat[train_num - 1][2] -= seats;
		/*bkd_2 += seats;
		bkd_3 += seats;*/
		break;
	case'3':
		seat[train_num - 1][0] -= seats;
		seat[train_num - 1][1] -= seats;
		seat[train_num - 1][2] -= seats;
		/*bkd_1 += seats;
		bkd_2 += seats;
		bkd_3 += seats;*/
		break;
	default: cout << "錯誤!!!!!!!\n";
	}
	//_____寫檔___________
	ofstream outfile("train.txt", ios::out);
	for (int i = 0; i < 6; i++) {
		outfile << seat[i][0] << " " << seat[i][1] << " " << seat[i][2] << endl;
	}

	outfile.close();//關檔
	//____________________
}


void Reservation::cancel(int train_num, char type, int num)
{
	switch (type)
	{
	case'1':
		seat[train_num - 1][0] += num;
		seat[train_num - 1][2] += num;
		/*bkd_1 -= num;
		bkd_3 -= num;*/
		break;
	case'2':
		seat[train_num - 1][1] += num;
		seat[train_num - 1][2] += num;
		/*bkd_2 -= num;
		bkd_3 -= num;*/
		break;
	case'3':
		seat[train_num - 1][0] += num;
		seat[train_num - 1][1] += num;
		seat[train_num - 1][2] += num;
	/*	bkd_1 -= num;
		bkd_2 -= num;
		bkd_3 -= num;*/
		break;
	default:cout << "錯誤!!!!!!\n";
	}
	//_____寫檔___________
	ofstream outfile("train.txt", ios::out);
	for (int i = 0; i < 6; i++) {
		outfile << seat[i][0] << " " << seat[i][1] << " " << seat[i][2] << endl;
	}

	outfile.close();//關檔
}
void Reservation::disp_status(void)
{
	for (int i = 0; i < 6; i++) {
		cout << "車號: " << i + 1 << endl;
		cout << "剩餘車位:" << endl;
		cout << "台北-台中: " << seat[i][0] << endl;
		cout << "台中-高雄: " << seat[i][1] << endl;
		cout << "台北-高雄: " << seat[i][2] << endl;
		cout << "---------------------------------------" << endl;
	}
}
int main()
{
	system("cls");
	//______讀檔______
	fstream fin("train.txt",ios::in);
	if (!fin) {
		cout << "無法讀入檔案\n";
		system("pause");
		return 0;
	}
	int i = 0;
	while (!fin.eof())//.EOF是確認讀檔讀到檔的最後面
	{
		fin >> seat[i][0] >> seat[i][1] >> seat[i][2];
		i++;
	}
	fin.close();//關檔
	//________________
	/*for (int i = 0; i < 6; i++) {
		cout << seat[i][0] << " " << seat[i][1] << " " << seat[i][2] << endl;
	}*/

	//-----計算時間----------
	tm structuredTime;
	time_t rawtime = time(0);
	localtime_s(&structuredTime, &rawtime);
	//-----------------------------------------------
	int year = structuredTime.tm_year + 1900;//1900起始時間
	int month = structuredTime.tm_mon + 1;//起始時間
	int day = structuredTime.tm_mday;
	
	int choice, seats;

	cout << "目前時間是: " << structuredTime.tm_year + 1900 << "-" << structuredTime.tm_mon + 1 << "-" << structuredTime.tm_mday << " "
		<< structuredTime.tm_hour << ":" << structuredTime.tm_min << ":" << structuredTime.tm_sec << endl;
	//-----計算時間 end----------

	//-------車次------------
	int num;
	cout << "目前車次:" << endl;
	cout << "1. 車號: 1 發車時間: 08:00 起點/終點: 台北/高雄" << endl <<
		"2. 車號: 2 發車時間: 09:00 起點/終點: 台北/高雄" << endl <<
		"3. 車號: 3 發車時間: 10:00 起點/終點: 台北/高雄" << endl <<
		"4. 車號: 4 發車時間: 11:00 起點/終點: 台北/高雄" << endl <<
		"5. 車號: 5 發車時間: 12:00 起點/終點: 台北/高雄" << endl <<
		"6. 車號: 6 發車時間: 13:00 起點/終點: 台北/高雄" << endl;
	cout << "請選擇車次" << endl;
	cin >> num;
	int s1 = 100;
	int s2 = 100;
	int s3 = 100;
	//時間 座位 寫死
	if (num == 1) {
		if (structuredTime.tm_hour >= 8) {
			cout << "已經發車了!";
			cout << "請選擇車次" << endl;
			cin >> num;
		}
	}
	else if (num == 2) {
		if (structuredTime.tm_hour >= 9) {
			cout << "已經發車了!";
			cout << "請選擇車次" << endl;
			cin >> num;
		}
	}
	else if (num == 3) {
		if (structuredTime.tm_hour >= 10) {
			cout << "已經發車了!";
			cout << "請選擇車次" << endl;
			cin >> num;
		}
	}
	else if (num == 4) {
		if (structuredTime.tm_hour >= 11) {
			cout << "已經發車了!";
			cout << "請選擇車次" << endl;
			cin >> num;
		}
	}
	else if (num == 5) {
		if (structuredTime.tm_hour >= 12) {
			cout << "已經發車了!";
			cout << "請選擇車次" << endl;
			cin >> num;
		}
	}
	else if (num == 6) {
		if (structuredTime.tm_hour >= 13) {
			cout << "已經發車了!";
			cout << "請選擇車次" << endl;
			cin >> num;
		}
	}

	while (num > 6) {
		cout << "請選擇車次" << endl;
		cin >> num;
	}

	/*else {
		cout << "車號:" << num << endl;
		cout << "在台北到台中的剩餘車位: ";
		cout << s1 << endl;
		cout << "在台中到高雄的剩餘車位: ";
		cout << s2 << endl;
		cout << "在台北到高雄的剩餘車位: ";
		cout << s3 << endl;
	}*/
	//-------車次 end------------

	Reservation Tr(num, s1, s2, s3);
	char cl_type;
	do
	{
		cout << "請選擇: ";
		cout << "\n 主頁面\n";
		cout << "1.訂位\n";
		cout << "2.取消訂位\n";
		cout << "3.目前訂位狀況\n";
		cout << "4.離開or重選車號\n";
		cin >> choice;
		cout << "\n";
		switch (choice)
		{
		case 1: cout << "請選擇你要搭乘的區間: " << endl << " 1. 台北到台中 2. 台中到高雄 3. 台北到高雄 " << endl;
			cin >> cl_type;
			cout << "\n需要多少位子: ";
			cin >> seats;
			cout << "\n";

			Tr.book(num,cl_type, seats);
			break;
		case 2:cout << "請選擇你要取消搭乘的區間: " << endl << " 1. 台北到台中 2. 台中到高雄 3. 台北到高雄 " << endl;
			cin >> cl_type;
			cout << "\n需要取消多少位子: ";
			cin >> seats;
			cout << "\n";
			Tr.cancel(num, cl_type, seats);
			break;
		case 3:Tr.disp_status();
			break;
		case 4:break;
		default: cout << "錯誤!!!!!!!\n";
		};
	} while (choice >= 1 && choice <= 3);
	getchar();
}
