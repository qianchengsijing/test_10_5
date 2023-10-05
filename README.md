# test_10_5
#include <stdio.h>
#include <stdlib.h>
//串的顺序存储(静态存储）
#define MAXSIZE 255
typedef struct{
	char ch[MAXSIZE];
	int length;
}SString;
//动态存储
typedef struct{
	char *ch;
	int length;
}HString;
void test(){
HString S;
S.ch = (char*)malloc(MAXSIZE*sizeof(char));
S.length = 0;
}
//链式存储
typedef struct StringNode{
	char ch;//定义一个结点存储一个字符char ch[4];
	struct StringNode* next;
}StringNode,*String;
//求子串
bool SubString(SString Sub,SString S,int pos,int len){
	if(pos+len-1 > S.length)
		return false;
	for(int i=pos;i<pos+len;i++){
		Sub.ch[i-pos+1] = S.ch[i];
	}
	Sub.length = len;
	return true;
}
//比较
int Strcompare(SString S,SString T){
	for(int i=1;i<=S.length && i<=T.length;i++){
		if(S.ch[i] != T.ch[i])
			return S.ch[i] - T.ch[i];
	}
	return S.length - T.length;
}
//定位
int Index(SString S,SString T){
	int i=1,n=Strlength(S),m=Strlength(T);
	SString Sub;
	while(i<n-m+1){
		SubString(Sub,S,i,m);
		if(Strcompare(Sub,T) != 0)
			++i;
		else
			return i;
		}
		return 0;
	}
