# MCSIM
#include <TH2.h>
#include <TStyle.h>
#include <TCanvas.h>
#include <iostream>
#include <cmath>
#include <random>
#include <chrono>
using namespace std;

int addition (float tot,float B){
Int_t newb=0;
float x=1;
float q = 6;
unsigned seed = std::chrono::system_clock::now().time_since_epoch().count();
std::default_random_engine generator (seed);
        for (Long64_t inc =1;inc<(1000);++inc){
                if ((B-inc)<=0) break;
                float D = 0;
                float Prob = (B-inc)/tot;
                float NoB[1000]={};
                std::binomial_distribution<int> distribution (tot,Prob);
//              cout<< distribution(generator)<< endl;
                for(Long64_t i=0; i<1000;++i){
                        NoB[i] = distribution(generator);
//                      cout<< "NoB="<< NoB[i]<<"    B'="<<B+inc<<"             D="<< D<<endl;
                        if (NoB[i] > B)
                        D=D+1;
                }

                if (D/1000<=(x/q)){
                newb =abs(inc);
                break;
                }



        }
return newb;

}
