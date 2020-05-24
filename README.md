# STACKOVER-FLOW-TAG-PREDICTOR

Problem Statemtent
Suggest the tags based on the content that was there in the question posted on Stackoverflow.

1.2 Source / useful links
Data Source : https://www.kaggle.com/c/facebook-recruiting-iii-keyword-extraction/data
Youtube : https://youtu.be/nNDqbUhtIRg

1.3 Real World / Business Objectives and Constraints
1. Predict as many tags as possible with high precision and recall.
2. Incorrect tags could impact customer experience on StackOverflow.
3. No strict latency constraints.

Train.csv contains 4 columns: Id,Title,Body,Tags.
Test.csv contains the same columns but without the Tags, which y
ou are to predict.
Size of Train.csv - 6.75GB
Size of Test.csv - 2GB

2.1.2 Example Data point
Title: Implementing Boundary Value Analysis of Software Testing
 in a C++ program?
Body :
#include<
 iostream>\n
 #include<
 stdlib.h>\n\n
 using namespace std;\n\n
 int main()\n
 {\n
 int n,a[n],x,c,u[n],m[n],e[n][4];\n

 cout<<"Enter the number of variables";\n
 cin>>n;\n\n
 cout<<"Enter the Lower, and Upper Limits
 of the variables";\n
 for(int y=1; y<n+1; y++)\n
 {\n
 cin>>m[y];\n
 cin>>u[y];\n
 }\n
 for(x=1; x<n+1; x++)\n
 {\n
 a[x] = (m[x] + u[x])/2;\n
 }\n
 c=(n*4)-4;\n
 for(int a1=1; a1<n+1; a1++)\n
 {\n\n
 e[a1][0] = m[a1];\n
 e[a1][1] = m[a1]+1;\n
 e[a1][2] = u[a1]-1;\n
 e[a1][3] = u[a1];\n
 }\n
 for(int i=1; i<n+1; i++)\
 for(int l=1; l<=i; l++)\n
 {\n
 if(l!=1)\n
 {\n
 cout<<a[l]<<"\\t";\n

 }\n
 }\n
 for(int j=0; j<4; j++)\n
 {\n
 cout<<e[i][j];\n
 for(int k=0; k<n-(i+1); k++)\n

 {\n
 cout<<a[k]<<"\\t";\n

 }\n
 cout<<"\\n";\n
 }\n
 } \n\n
 system("PAUSE");\n
 return 0; \n
 }\n

\n\n

2.2.1 Type of Machine Learning Problem
It is a multi-label classification problem

Multi-label Classification: Multilabel classification assigns to each sample a set of target labels.

This can be thought as predicting properties of a data-point that are not mutually exclusive, such

as topics that are relevant for a document. A question on Stackoverflow might be about any of C,

Pointers, FileIO and/or memory-management at the same time or none of these. 

2.2.2 Performance metric
Micro-Averaged F1-Score (Mean F Score) : The F1 score can be interpreted as a weighted

average of the precision and recall, where an F1 score reaches its best value at 1 and worst

score at 0. The relative contribution of precision and recall to the F1 score are equal. The formula

for the F1 score is:
F1 = 2 * (precision * recall) / (precision + recall)

In the multi-class and multi-label case, this is the weighted average of the F1 score of each
class.

'Micro f1 score':
Calculate metrics globally by counting the total true positives, false negatives and false positives.

This is a better metric when we have class imbalance.

'Macro f1 score':
Calculate metrics for each label, and find their unweighted mean. This does not take label
imbalance into account.

https://www.kaggle.com/wiki/MeanFScore
http://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html

Hamming loss : The Hamming loss is the fraction of labels that are incorrectly predicted.
https://www.kaggle.com/wiki/HammingLoss
