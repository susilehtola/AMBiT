add_library(MBPT OBJECT BruecknerDecorator.cpp
             BruecknerSigmaCalculator.cpp CoreMBPTCalculator.cpp
             MBPTCalculator.cpp OneElectronMBPT.cpp
             Sigma3Calculator.cpp SigmaPotential.cpp
             TwoElectronCoulombOperator.cpp ValenceMBPTCalculator.cpp)
