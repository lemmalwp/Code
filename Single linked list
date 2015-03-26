#include <stdio.h>
#include <malloc.h>
#define ERROR 0
#define OK 1
typedef int Elemtype;
typedef int Status;
//定义单链表的储存结构
typedef struct Node
{
	Elemtype data;
	struct Node *next;
}Listnode;
Node Listhead;
Node *Listpointer;
//创建单链表
Node ListCreat(Node *Listpointer, int Elemnumber)
{
	//输入Elemnumber个元素的值，建立带表头结点的单链表
	Node *Linknew,*Linkend;
	Listpointer= (Node*) malloc(sizeof(Node));//创建头结点且内容为空
	Node *Linkhead = Listpointer;
	Linkhead->next = NULL;
	Linkend = Linkhead;//尾指针指向头结点
	for (int count = 0; count < Elemnumber; count++)//创建Elemnumber个结点
	{
		Linknew = (Node*)malloc(sizeof(Node));
		printf_s("Please enter the elem:\n");
		scanf_s("%d", &Linknew->data);
		Linknew->next = NULL;
		Linkend->next = Linknew;//尾指针所在结点的Next指向新结点
		Linkend = Linkend->next;//尾指针指向最新加入的结点
	}
	return (*Listpointer);
}
//向链表插入元素
Status ListInsert(Node &Listhead, int Elemposition, Elemtype Elem)
{
	//在带头结点的单链表中第Elemposition个位置前插入元素Elem的结点
	Node *Linkposition = &Listhead;
	int count = 0;
	for (; Linkposition&&count < Elemposition - 1; count++)//找到要插入位置的前一个位置
		Linkposition = Linkposition->next;
	if (!Linkposition || count > Elemposition - 1)//超出表范围返回ERROR
	{
		printf_s("\nfail!");
		return ERROR;
	}
	Node *Linknew = (Node*)malloc(sizeof(Node));//创建新结点
	Linknew->data = Elem;
	Linknew->next = Linkposition->next;//新结点指针域指向Linkposition的下一个结点
	Linkposition->next = Linknew;//Linkposition指针域指向新结点
	return OK;
}
//从链表删除元素
Status ListDelete(Node &Listhead, int Elemposition, Elemtype &Elem)
{
	//从链表中删除第Elemposition个位置的元素，用Elem返回
	Node *Linkposition = &Listhead;
	int count = 0;
	for (; Linkposition->next&&count < Elemposition - 1; count++)//找到第Elemposition-1个结点
		Linkposition = Linkposition->next;
	if (!(Linkposition->next) || count > Elemposition - 1)//如果超出链表位置则返回ERROR
	{
		printf_s("\nfail!");
		return ERROR;
	}
	Node *Linkdelete = Linkposition->next;//创建指针指向第Elemposition个结点
	Linkposition->next = Linkdelete->next;//第Elemposition-1个结点指针域指向第Elemposition+1个结点
	Elem = Linkdelete->data;//用Elem返回删除结点的数据
	free(Linkdelete);//释放第Elemposition个结点的内存
	return OK;
}
//销毁单链表
void ListDestory(Node *Listpointer)
{
	Listpointer = Listhead.next;
	Node *Linktemp = Listpointer;
	for (; Listpointer;)
	{
		Listpointer = Listpointer->next;
		free(Linktemp);
		Linktemp = Listpointer;
	}
	free(&Listhead);
}
//打印单链表
void ListPrint(Node &Listhead)
{
	//若下个结点存在，打印下一个结点的数值，然后将指针指向下一个结点
	Node *Linkposition = &Listhead;
	printf_s("\nThe List is as below:\n");
	for (; Linkposition->next; Linkposition = Linkposition->next)
		printf("%d ", Linkposition->next->data);
}
//选择功能
void Listmenu(int function)
{
	//选择四个不同功能
	int Elemnumber = 0, Elemposition = 0;
	Elemtype Elemcontent = 0;
	switch (function)
	{
	case 1:
		printf_s("\nPlease enter the number of elems you want to put into the List:");
		scanf_s("%d", &Elemnumber);
		Listhead = ListCreat(Listpointer, Elemnumber);
		ListPrint(Listhead);
		break;
	case 2:
		printf_s("\nPlease enter the number of elems you want to insert:");
		scanf_s("%d", &Elemnumber);
		for (int count = 0; count < Elemnumber; count++)
		{
			printf_s("\nPlease enter the position:");
			scanf_s("%d", &Elemposition);
			printf_s("\nPlease enter the Elem:");
			scanf_s("%d", &Elemcontent);
			ListInsert(Listhead, Elemposition, Elemcontent);
			ListPrint(Listhead);
		}
		break;
	case 3:
		printf_s("\nPlease enter the number of elems you want to delete:");
		scanf_s("%d", &Elemnumber);
		for (int count = 0; count < Elemnumber; count++)
		{
			printf_s("\nPlease enter the position:");
			scanf_s("%d", &Elemposition);
			ListDelete(Listhead, Elemposition, Elemcontent);
			ListPrint(Listhead);
		}
		break;
	case 4:
		ListDestory(Listpointer);
		printf_s("\nThe list is destoried.");
		break;
	default:
		break;
	}
}
//主函数
int main()
{
	for (int function = -1; function;)
	{
		printf_s("\n\nPlease choose the functions below:\n");//输出菜单
		printf_s("1.Create a new list.\n");
		printf_s("2.Insert elems to the list.\n");
		printf_s("3.Delete elems from the list.\n");
		printf_s("4.Destory the list.\n");
		printf_s("0.Exit the programn.\n");
		scanf_s("%d", &function);
		if (!function)
			break;
		Listmenu(function);
	}
	return OK;
}
