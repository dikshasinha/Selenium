using System;
using System.Linq;
using System.Text;
using System.Collections.Generic;
using FluentAssertions.Collections;
using TechTalk.SpecFlow;
using OpenQA.Selenium;
using OpenQA.Selenium.Remote;
using OpenQA.Selenium.IE;
using OpenQA.Selenium.Support.UI;
using OpenQA.Selenium.Internal;


namespace MerretDemoproject
{
    class LoginPage
    {
        private IWebDriver driver;

        internal LoginPage(IWebDriver driver) { this.driver = driver; }

        By InputName = By.Id("UserName");
        By InputPassword = By.Id("Password");
        By ButtonLogin = By.Id("btnLogin");
        By dropdownenv = By.Id("ContentPlaceHolder1_ddlEnviroment");
        By ButtinEnter = By.Id("ContentPlaceHolder1_btnEnvironment");
        By dropdownsession = By.Id("ddlSessions");
        By buttonSession = By.Id("btnSession");

        internal void Login()
        {
            driver.FindElement(InputName).SendKeys("Tdiksha");
            driver.FindElement(InputPassword).SendKeys("password");
            driver.FindElement(ButtonLogin).Click();
            SelectElement S = new SelectElement(driver.FindElement(dropdownenv));
            S.SelectByText("ASOS Test B.T.- Merret v6.5");
            driver.FindElement(ButtinEnter).Click();

            SelectElement S2 = new SelectElement(driver.FindElement(dropdownsession));
            if (driver.FindElements(dropdownsession).Count > 0)
            {
                S2.SelectByText("Tdiksha");
                driver.FindElement(buttonSession).Click();
            }
        }

