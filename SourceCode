#include <stdlib.h>
#include <QtGui>
#include <time.h>
#include <math.h>
#include <iostream>
using namespace std;

int Amount = 250;//money: we assume it is 250
int AmountB[8]= {0,0,0,0,0,0,0,0};//Money transferred to array
int UniqueID[10][8];//Uniqueness String
int IdentityString[10][10][8];//IdentityString
int ISL[10][10][8];//IdentityString Leftaprt
int ISR[10][10][8];//IdentityString Rightpart
int BC[10][10][8];//Bit Commitment
int BS1[8];//Blind Signature1
int BS2[10][10][8];//Blind Signature2
int BS[8];//BS1 XOR BS2
int UID[8];
int BS3[8];
int M=0;
int k = 6, e = 2,n = 8;
int d = 3;
int ISFB[10][10][8];//Revealed Identity String


QString strAmount,strAmountB,strUniqueID,strIdentityString,strISL,
strISR,strBC,strBS1,strBS2,strBS,strUID,strBS3,strM,strk,strn,strd,
strt,strsign, strs,strISFB = "";

QWizardPage *Description()
{
    QWizardPage *page = new QWizardPage;
    page->setTitle("Description");

    QLabel *label = new QLabel("This GUI will demontrate a walkthrough Digital Cash implementation with Deffie-Hellmann encryption and decryption.");
    label->setWordWrap(true);

    QVBoxLayout *layout = new QVBoxLayout;
    layout->addWidget(label);
    page->setLayout(layout);

    return page;
}


QWizardPage *MoneyOrder()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("MoneyOrder");

    QLabel *amountLabel = new QLabel("Amount:");
    QLineEdit *amountLineEdit = new QLineEdit;
    amountLineEdit->setText(QString::number(Amount,10));
    amountLineEdit->setReadOnly(true);
    QGridLayout *layout = new QGridLayout;
    layout->addWidget(amountLabel, 0, 0);
    layout->addWidget(amountLineEdit, 0, 1);

    for (int i = 0; i < 8; i++){
        AmountB[7 - i] = Amount % 2;
        Amount = Amount / 2;
    }

    for(int i =0 ; i < 8 ;i++)
        strAmountB.append(QString::number(AmountB[i],10));

    QLabel *strAmountLabel = new QLabel("Amount Binary:");
    QLineEdit *strAmountLineEdit = new QLineEdit;
    strAmountLineEdit->setText(strAmountB);
    strAmountLineEdit->setReadOnly(true);
    layout->addWidget(strAmountLabel, 1, 0);
    layout->addWidget(strAmountLineEdit, 1, 1);


    page->setLayout(layout);

    return page;
}

QWizardPage *IdentityStringPage()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("IdentityString");


    QTextEdit *txtEdit = new QTextEdit;

    txtEdit->setReadOnly(true);
    QGridLayout *layout = new QGridLayout;

    layout->addWidget(txtEdit, 0, 0);

    for (int m = 0; m < 10; m++)
    {
        for (int n = 0; n < 10; n++)
        {
            for (int k = 0; k < 8; k++)
            {

                IdentityString[m][n][k] = (rand() + 21) % 2;
                strIdentityString.append(QString::number(IdentityString[m][n][k],10));

            }
        }
    }
    txtEdit->setText(strIdentityString);
    page->setLayout(layout);

    return page;
}

QWizardPage *IdentityStringLeftPage()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("IdentityStringLeft");


    QTextEdit *txtEdit = new QTextEdit;

    txtEdit->setReadOnly(true);
    QGridLayout *layout = new QGridLayout;

    layout->addWidget(txtEdit, 0, 0);

    for (int m = 0; m < 10; m++)
    {
        for (int n = 0; n < 10; n++)
        {
            for (int k = 0; k < 8; k++)
            {

                ISL[m][n][k] = (rand() + 12) % 2;
                strISL.append(QString::number(ISL[m][n][k],10));

            }
        }
    }
    txtEdit->setText(strISL);
    page->setLayout(layout);

    return page;
}

QWizardPage *IdentityStringRightPage()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("IdentityStringRight");


    QTextEdit *txtEdit = new QTextEdit;

    txtEdit->setReadOnly(true);
    QGridLayout *layout = new QGridLayout;

    layout->addWidget(txtEdit, 0, 0);

    for (int m = 0; m < 10; m++)
    {
        for (int n = 0; n < 10; n++)
        {
            for (int k = 0; k < 8; k++)
            {

                ISR[m][n][k] = (IdentityString[m][n][k] + ISL[m][n][k]) % 2;
                strISR.append(QString::number(ISR[m][n][k],10));

            }
        }
    }
    txtEdit->setText(strISR);
    page->setLayout(layout);

    return page;
}

QWizardPage *BitCommitPage()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("BitCommit");


    QTextEdit *txtEdit = new QTextEdit;

    txtEdit->setReadOnly(true);
    QGridLayout *layout = new QGridLayout;

    layout->addWidget(txtEdit, 0, 0);

    for (int m = 0; m < 10; m++)
    {
        for (int n = 0; n < 10; n++)
        {
            for (int k = 0; k < 8; k++)
            {

                BC[m][n][k] = (ISL[m][n][k] + ISR[m][n][k] + 1) % 2;
                strBC.append(QString::number(BC[m][n][k],10));

            }
        }
    }
    txtEdit->setText(strBC);
    page->setLayout(layout);

    return page;
}

QWizardPage *UniqueIDPage()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("UniqueID");


    QTextEdit *txtEdit = new QTextEdit;

    txtEdit->setReadOnly(true);
    QGridLayout *layout = new QGridLayout;

    layout->addWidget(txtEdit, 0, 0);

    for (int m = 0; m < 10; m++)
    {
        for (int n = 0; n < 8; n++)
        {
                UniqueID[m][n] = (rand() + 10) % 2;
                strUniqueID.append(QString::number(UniqueID[m][n],10));
        }
    }
    txtEdit->setText(strUniqueID);
    page->setLayout(layout);

    return page;
}

QWizardPage *FirstUniqueIDandBlindSignPage()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("FirstUniqueID and Blind Signature 1");

    QLabel *FirstUniqueIDLabel = new QLabel("FirstUniqueID:");
    QLabel *BS1Label = new QLabel("Binary Signature 1:");

    QLineEdit *FirstUniqueIDLineEdit = new QLineEdit;
    QLineEdit *BS1LineEdit = new QLineEdit;


    FirstUniqueIDLineEdit->setReadOnly(true);
    BS1LineEdit->setReadOnly(true);

    QGridLayout *layout = new QGridLayout;
    layout->addWidget(FirstUniqueIDLabel, 0, 0);
    layout->addWidget(FirstUniqueIDLineEdit, 0, 1);
    layout->addWidget(BS1Label, 1, 0);
    layout->addWidget(BS1LineEdit, 1, 1);


   for (int i = 0; i < 8; i++){
                UID[i] = UniqueID[0][i];
                BS1[i] = (AmountB[i] + UID[i]) % 2;

                strUID.append(QString::number(UID[i],10));
                strBS1.append(QString::number(BS1[i],10));
    }

    FirstUniqueIDLineEdit->setText(strUID);
    BS1LineEdit->setText(strBS1);

    page->setLayout(layout);

    return page;
}

QWizardPage *BlindSignature2Page()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("Blind Signature 2");


    QTextEdit *txtEdit = new QTextEdit;

    txtEdit->setReadOnly(true);
    QGridLayout *layout = new QGridLayout;

    layout->addWidget(txtEdit, 0, 0);

    for (int m = 0; m < 10; m++)
    {
        for (int n = 0; n < 10; n++)
        {
            for (int k = 0; k < 8; k++)
            {

                BS2[m][n][k] = (BC[m][n][k] + ISL[m][n][k]) % 2;
                strBS2.append(QString::number(BS2[m][n][k],10));

            }
        }
    }
    txtEdit->setText(strBS2);
    page->setLayout(layout);

    return page;
}

QWizardPage *BlindSignature3Page()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("Blind Signature 3");


    QTextEdit *txtEdit = new QTextEdit;

    txtEdit->setReadOnly(true);
    QGridLayout *layout = new QGridLayout;

    layout->addWidget(txtEdit, 0, 0);

        for (int i = 0; i < 10; i++)
        {
            for (int j = 0; j < 8; j++)
            {

                BS3[j] = BS2[0][i][j];
                strBS3.append(QString::number(BS3[j],10));

            }
        }

    txtEdit->setText(strBS3);
    page->setLayout(layout);

    return page;
}

QWizardPage *BlindSignaturePage()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("BlindSignature");

    QLabel *BlindSignatureLabel = new QLabel("BlindSignature:");
    QLabel *MLabel = new QLabel("M:");
    QLabel *tLabel = new QLabel("Alice's Signature:");
    QLabel *signLabel = new QLabel("Bank's Signature:");
    QLabel *sLabel = new QLabel("Unblind:");

    QLineEdit *BlindSignatureLineEdit = new QLineEdit;
    QLineEdit *MLineEdit = new QLineEdit;
    QLineEdit *tLineEdit = new QLineEdit;
    QLineEdit *signLineEdit = new QLineEdit;
    QLineEdit *sLineEdit = new QLineEdit;

    BlindSignatureLineEdit->setReadOnly(true);
    MLineEdit->setReadOnly(true);
    tLineEdit->setReadOnly(true);
    signLineEdit->setReadOnly(true);
    sLineEdit->setReadOnly(true);

    QGridLayout *layout = new QGridLayout;
    layout->addWidget(BlindSignatureLabel, 0, 0);
    layout->addWidget(BlindSignatureLineEdit, 0, 1);
    layout->addWidget(MLabel, 1, 0);
    layout->addWidget(MLineEdit, 1, 1);
    layout->addWidget(tLabel, 2, 0);
    layout->addWidget(tLineEdit, 2, 1);
    layout->addWidget(signLabel, 3, 0);
    layout->addWidget(signLineEdit, 3, 1);
    layout->addWidget(sLabel, 4, 0);
    layout->addWidget(sLineEdit, 4, 1);



   for (int i = 0; i < 8; i++){
       BS[i] = (BS1[i] + BS3[i]) % 2;
       strBS.append(QString::number(BS[i],10));
       if (BS[i] == 1)
           M = M + pow(2, 7-i);
    }
    strM = QString::number(M,10);

    int t = (M*(int)pow(k, e)) % n;
    strt = QString::number(t,10);

    int sign = (int)pow(M*(int)pow(k, e), d)%n;
    strsign = QString::number(sign,10);

    int s = ((t*d) / k) % n;
    strs = QString::number(s,10);
    BlindSignatureLineEdit->setText(strUID);
    MLineEdit->setText(strM);
    tLineEdit->setText(strt);
    signLineEdit->setText(strsign);
    sLineEdit->setText(strs);

    page->setLayout(layout);

    return page;
}

QWizardPage *RevealIdentityStringPage()
{

    QWizardPage *page = new QWizardPage;
    page->setTitle("Reveal Identity String");


    QTextEdit *txtEdit = new QTextEdit;

    txtEdit->setReadOnly(true);
    QGridLayout *layout = new QGridLayout;

    layout->addWidget(txtEdit, 0, 0);

    for (int m = 0; m < 10; m++)
    {
        for (int n = 0; n < 10; n++)
        {
            for (int k = 0; k < 8; k++)
            {

                ISFB[m][n][k] = (ISR[m][n][k] + ISL[m][n][k]) % 2;
                strISFB.append(QString::number(ISFB[m][n][k],10));
            }
        }
    }
    txtEdit->setText(strISFB);
    page->setLayout(layout);

    return page;
}

QWizardPage *End()
{
    QWizardPage *page = new QWizardPage;
    page->setTitle("End");

    return page;
}

int main(int argc, char *argv[])
{
    QApplication app(argc, argv);
    srand(time(NULL));
    QWizard DigitalCash;
    DigitalCash.addPage(Description());
    DigitalCash.addPage(MoneyOrder());
    DigitalCash.addPage(IdentityStringPage());
    DigitalCash.addPage(IdentityStringLeftPage());
    DigitalCash.addPage(IdentityStringRightPage());
    DigitalCash.addPage(BitCommitPage());
    DigitalCash.addPage(UniqueIDPage());
    DigitalCash.addPage(FirstUniqueIDandBlindSignPage());
    DigitalCash.addPage(BlindSignature2Page());
    DigitalCash.addPage(BlindSignature3Page());
    DigitalCash.addPage(BlindSignaturePage());
    DigitalCash.addPage(RevealIdentityStringPage());
    DigitalCash.addPage(End());

    DigitalCash.setWindowTitle("Digital Cash");

    DigitalCash.show();


    return app.exec();
}

