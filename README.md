Driver Loader / Injection / Rootkit in C++ for Windows
==============

Intro
--------------
I wrote this project back in 2011 when I was playing a bit with Injections.
The class is used to Inject Drivers's / Rootkits into Windows Kernel.

CDriver_Loader has methods to Load and Eject from the Windows Kernel.


Usage 
---------------
	CDriver_Loader* driver;
	try 
	{
		driver = new CDriver_Loader();
		driver->InitSvc(L"c://rootkit.sys", L"driver", L"driver", SERVICE_DEMAND_START);
		cout << "Driver Loaded!" << endl;
 
		driver->CreateSvc();
		cout << "Driver Created!" << endl;

		driver->StartSvc();
		cout << "Driver Started!" << endl;

		cout << "Press any key to unload driver...";
		cin.get();
		driver->UnloadSvc();
		cout << "Driver unloaded!" << endl;
	}
	catch (std::exception &e) 
	{
		cout << "Error:" << e.what() << endl;
	}

	delete driver;
