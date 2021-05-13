#include<bits/stdc++.h>
using namespace std;

void delAll(stack<pair<char, int>>& st){
    while(!st.empty()){
        st.pop();
    }
}

int main(){

    string str;
    cin >> str;
    int n = str.size(), M_l_st = -1, M_r_st = 0, M_st = 0, M = 0, M_l, M_r;
    int numofOpen[n] = {0};
    int mostLeftBalancedWith[n];
    memset(mostLeftBalancedWith, -1, sizeof mostLeftBalancedWith);

    for (int i = 0; i < n; ++i){
        numofOpen[i] = str[i] == '[';
    }

    for (int i = 1; i < n; ++i){
        numofOpen[i] += numofOpen[i-1];
    }

    stack<pair<char, int>> st;

    for (int i = 0; i < n; ++i){
        if(str[i] == '(' || str[i] == '['){
            st.push({str[i], i});
        }else if(!st.empty()){
            if((str[i] == ')' && st.top().first == '(') ||
               (str[i] == ']' && st.top().first == '[')){

                int m_st, l_st, r_st;
                l_st = st.top().second;
                r_st = i;

                if(l_st > 0 && mostLeftBalancedWith[l_st-1] != -1){
                    l_st = mostLeftBalancedWith[l_st-1];
                }

                m_st = numofOpen[r_st] + (l_st > 0 ?  -numofOpen[l_st-1] : 0);

                if(M_st <= m_st){
                    M_st = m_st;
                    M_l_st = l_st;
                    M_r_st = r_st;
                }
                mostLeftBalancedWith[M_r_st] = M_l_st;
                st.pop();
            }else{ // substring from 0 to i not balanced.
                if(M < M_st){
                    M = M_st;
                    M_l = M_l_st;
                    M_r = M_r_st;
                }
                M_st = 0;
                delAll(st);
            }
        }else{
            if(M < M_st){
                M = M_st;
                M_l = M_l_st;
                M_r = M_r_st;
            }
            M_st = 0;
        }
    }
    if(M < M_st){
        M = M_st;
        M_l = M_l_st;
        M_r = M_r_st;
    }

    if(M){
        cout << M << "\n" << str.substr(M_l, M_r-M_l+1) << "\n";
    }else{
        cout << "0\n" << "\n\n";
    }

    return 0;
}
