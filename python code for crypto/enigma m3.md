### Decode cipher for Enigma Machine3 for Reflector B

    class EnigmaM3:
        def __init__(self, rotors, reflector, ring_settings, plugboard):
            self.rotors = rotors
            self.reflector = reflector
            self.ring_settings = ring_settings
            self.plugboard = plugboard
            self.alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        
        def process_text(self, text, positions):
            result = []
            for letter in text.upper():
                if letter in self.alphabet:
                    letter = self.plugboard_swap(letter)
                    letter = self.pass_through_rotors(letter, positions)
                    letter = self.reflector_swap(letter)
                    letter = self.pass_back_through_rotors(letter, positions)
                    letter = self.plugboard_swap(letter)
                    result.append(letter)
                    self.rotate_rotors(positions)
            return ''.join(result)
    
        def plugboard_swap(self, letter):
            for swap in self.plugboard:
                if letter in swap:
                    return swap[0] if letter == swap[1] else swap[1]
            return letter
        
        def pass_through_rotors(self, letter, positions):
            for i in range(3):
                offset = (self.alphabet.index(positions[i]) + self.alphabet.index(letter)) % 26
                letter = self.rotors[i][offset]
            return letter
        
        def pass_back_through_rotors(self, letter, positions):
            for i in range(2, -1, -1):
                offset = self.rotors[i].index(letter) - self.alphabet.index(positions[i])
                letter = self.alphabet[offset % 26]
            return letter
        
        def reflector_swap(self, letter):
            return self.reflector[self.alphabet.index(letter)]
        
        def rotate_rotors(self, positions):
            if positions[2] == 'Z':
                if positions[1] == 'Z':
                    positions[0] = self.alphabet[(self.alphabet.index(positions[0]) + 1) % 26]
                positions[1] = self.alphabet[(self.alphabet.index(positions[1]) + 1) % 26]
            positions[2] = self.alphabet[(self.alphabet.index(positions[2]) + 1) % 26]
    
    rotor_I = "EKMFLGDQVZNTOWYHXUSPAIBRCJ"
    rotor_II = "AJDKSIRUXBLHWTMCQGZNPYFVOE"
    rotor_III = "BDFHJLCPRTXVZNYEIWGAKMUSQO"
    reflector_B = "YRUHQSLDPXNGOKMIEBFZCWVJAT"
    
    plugboard_connections = ["AG", "BH"]
    ring_settings = [4, 4, 4]
    rotor_positions = list("ABC")
    ciphertext = "ymnjp znmjo gteqj cjwwh qljtd nprmp g"
    enigma = EnigmaM3(
        rotors=[rotor_I, rotor_II, rotor_III],
        reflector=reflector_B,
        ring_settings=ring_settings,
        plugboard=plugboard_connections
    )
    
    plaintext = enigma.process_text(ciphertext.replace(" ", ""), rotor_positions)
    formatted_plaintext = plaintext.lower().replace(" ", "_")
    flag = f"QUESTCON{{{formatted_plaintext}}}"
    print("Decoded Flag:", flag)

