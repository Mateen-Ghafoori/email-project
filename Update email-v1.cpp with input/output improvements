//
//  main.cpp
//  email.cpp
//  Created by Mateen Ghafoori on 5/6/25

#include <iostream>
#include <fstream>
#include <string>
#include <set>
using namespace std;

int main()
{
    string defulinput1 = "dvc1.txt";
    string defulinput2 = "dvc2.txt";
    string defuloutput = "dvc3.txt";
    
    string firstInputfile;
    string secondInputfile;
    string outputFile;
    
    cout << "Enter your first input file:" << endl;
    getline(cin, firstInputfile);
    if(firstInputfile.empty())
    {
        firstInputfile = defulinput1;
    }
    
    cout << "Enter your second input file:" << endl;
    getline(cin, secondInputfile);
    if(secondInputfile.empty())
    {
        secondInputfile = defulinput2;
    }
    
    cout << "Enter your output file:" << endl;
    getline(cin, outputFile);
    if(outputFile.empty())
    {
        outputFile = defuloutput;
    }
    
    string path = "/Users/mateenghafoori/Desktop/";
    ifstream fin1(path + firstInputfile);
    ifstream fin2(path + secondInputfile);
    
    if (!fin1.is_open() || !fin2.is_open())
    {
        cerr << "Error: Could not open one or both input files." << endl;
        return 1;
    }
    
    set<string> emails;
    string word;
    string line;
    
    
    while(fin1 >> word)
    {
        if(word.find('@') != string :: npos)
        {
            emails.insert(word);
        }
        else
        {
            while (getline(fin1, line))
            {
                if(line.find('@') != string :: npos)
                {
                    size_t start = line.rfind(":", line.find('@'));
                    size_t end = line.find("'", line.find('@'));
                    if(start != string :: npos && end != string :: npos)
                    {
                        string email = line.substr(start + 1, end-start -1);
                        emails.insert(email);
                    }
                }
            }
            
        }
    }
    
    fin1.close();
    
    while(fin2 >> word)
    {
        if(word.find('@') != string :: npos)
        {
            emails.insert(word);
        }
        else
        {
            while(getline(fin2, line))
            {
                if(line.find('@') != string :: npos)
                {
                    size_t start = line.rfind(":", line.find('@'));
                    size_t end = line.find("'", line.find('@'));
                    if(start != string :: npos && end != string :: npos)
                    {
                        string email = line.substr(start + 1, end-start -1);
                        emails.insert(email);
                    }
                }
            }
        }
    }
    fin2.close();
    
    if(emails.empty())
    {
        cout << "No email found it " << endl;
        return 0;
    }
    
    ofstream fout(path + outputFile);
    for ( const auto & email : emails)
    {                                                         
        cout << email << ";"<< " ";
        fout << email << ";"<< " ";
    }
    
    cout <<"we found " << emails.size() << " email addresses saved to " << outputFile << endl;              
    cout << "Please use the BCC(Blind Carbon Copy) field when sending the email to protect everyone's privacy" << "." << endl;

    fout.close();
    return 0;
}

