class HangpersonGame

  # add the necessary class methods, attributes, etc. here
  # to make the tests in spec/hangperson_game_spec.rb pass.

  # Get a word from remote "random word" service

  # def initialize()
  # end
  
  def initialize(word)
    @word = word
    @guesses = ''
    @wrong_guesses = ''
  end
  
  attr_accessor :word, :guesses, :wrong_guesses
  
  def guess(letter)
    # raise error if argument is invalid
    raise ArgumentError if (letter.to_s == '') or !(letter =~ /[[:alpha:]]/ )
    # we don't need case-sensitive check
    letter.downcase!
    # check letter and if it doesn't exist, add it in the corresponding variable
    if @word.include?(letter) 
      if @guesses.include?(letter)
        return false
      else
        @guesses += letter
      end
    else 
      if @wrong_guesses.include?(letter)
        return false
      else
        @wrong_guesses += letter 
      end
    end
    true
  end
  
  def word_with_guesses
    wwg=''
    @word.each_char do |letter|
      if @guesses.include?(letter)
        wwg += letter
      else
        wwg += '-'
      end
    end
    wwg
  end
  
  def check_win_or_lose
    if self.word_with_guesses == @word
      return :win
    elsif @wrong_guesses.length == 7
      return :lose
    else
      return :play
    end
  end

  def self.get_random_word
    require 'uri'
    require 'net/http'
    uri = URI('http://watchout4snakes.com/wo4snakes/Random/RandomWord')
    Net::HTTP.post_form(uri ,{}).body
  end

end